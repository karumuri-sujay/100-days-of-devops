### Task:

The Nautilus application development team was working on a git repository `/usr/src/kodekloudrepos/ecommerce` present on `Storage server` in `Stratos DC`.
 This was just a test repository and one of the developers just pushed a
 couple of changes for testing, but now they want to clean this
repository along with the commit history/work tree, so they want to
point back the `HEAD` and the branch itself to a commit with message `add data.txt file`.  Find below more details:

1. In `/usr/src/kodekloudrepos/ecommerce` git repository, reset the git commit history so that there are only two commits in the commit history i.e `initial commit` and `add data.txt file`.
2. Also make sure to push your changes.

#### Solution:

Run these below commands

```
    1  cd /usr/src/kodekloudrepos/ecommerce/
    2  ls
    3  git log
    4  git log --oneline
    5  git reset --hard d10b497
    6  git status
    7  git push --force
    8  history
```
