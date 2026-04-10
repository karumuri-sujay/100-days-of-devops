### Task:

The Nautilus application development team has been working
 on a project repository /opt/games.git. This repo is cloned at
/usr/src/kodekloudrepos on storage server in Stratos DC. They recently
shared the following requirements with DevOps team:

> One of the developers is working on feature branch and
> their work is still in progress, however there are some changes which
> have been pushed into the master branch, the developer now wants to
> rebase the feature branch with the master branch without loosing any
> data from the feature branch, also they don't want to add any merge
> commit by simply merging the master branch into the feature branch.
> Accomplish this task as per requirements mentioned.

#### Solution:

Run the below commands

```
    1  cd /usr/src/kodekloudrepos/blog
    2  ls
    3  git branch
    4  git rebase master
    5  git push --force --set-upstream origin feature
```
