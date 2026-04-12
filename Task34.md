### Task:

The Nautilus application development team was working on a git repository `/opt/blog.git` which is cloned under `/usr/src/kodekloudrepos`  directory present on `Storage server` in `Stratos DC`. The team want to setup a hook on this repository, please find below more details:

* Merge the `feature` branch into the `master` branch, but before pushing your changes complete below point.
* Create a `post-update` hook in this git repository so that whenever any changes are pushed to the `master` branch, it creates a release tag with name `release-2023-06-15`, where `2023-06-15` is supposed to be the current date. For example if today is `20th June, 2023` then the release tag must be `release-2023-06-20`. Make sure you test the hook at least once and create a release tag for today's release.

#### Solution:

Run the below command

```
    1  cd /usr/src/kodekloudrepos/official/
    2  git fetch origin
    3  git checkout master
    4  git merge feature
    5  cd /opt/official.git/hooks/
    6  printf '%s\n' '#!/usr/bin/env bash
set -euo pipefail

DATE=$(date +%F)
TAG="release-$DATE"

# Only when master was updated
for ref in "$@"; do
  if [ "$ref" = "refs/heads/master" ]; then
    NEWREV=$(git rev-parse refs/heads/master)
    if git rev-parse -q --verify "refs/tags/$TAG" >/dev/null; then
      echo "Tag $TAG already exists; skipping."
    else
      git tag "$TAG" "$NEWREV"
      echo "Created tag: $TAG at $NEWREV"
    fi
  fi
done

# Keep server info updated (useful for dumb HTTP)
exec git update-server-info
' | tee post-update >/dev/null
    7  chmod +x post-update
    8  cd
    9  cd /usr/src/kodekloudrepos/official/
   10  git push origin master
   11  git ls-remote --tags origin | grep "release-$(date +%F)" || echo "Tag not found yet"
```
