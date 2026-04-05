### Task:


1. In `/usr/src/kodekloudrepos/beta`  git repository, revert the latest commit `( HEAD )` to the previous commit (JFYI the previous commit hash should be with `initial commit` message ).
2. Use `revert beta` message (please use all small letters for commit message) for the new revert commit.

#### Solution:

Run the below commands

```
git revert HEAD -n
git commit -m "revert beta message"
```
