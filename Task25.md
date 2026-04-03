### Task:

The Nautilus application development team has been working on a project repository `/opt/official.git`. This repo is cloned at `/usr/src/kodekloudrepos` on `storage server` in `Stratos DC`. They recently shared the following requirements with DevOps team:

Create a new branch `devops` in `/usr/src/kodekloudrepos/official` repo from `master` and copy the `/tmp/index.html` file (present on `storage server` itself) into the repo. Further, `add/commit` this file in the new branch and merge back that branch into `master` branch. Finally, push the changes to the origin for both of the branches.

#### Solution:

Run the commands in the sequence

```
    1  cd
    2  cd /usr/src/kodekloudrepos/official/
    3  ls
    4  git branch
    5  git branch devops master
    6  git checkout devops
    7  git branch
    8  cp /tmp/index.html .
    9  git add .
   10  git commit -m "added tmp file"
   11  git switch master
   12  git merge devops
   13  git push
   14  git push origin master
```
