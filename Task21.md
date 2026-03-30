### Task:

1. Utilize `yum` to install the `git` package on the `Storage Server`.
2. Create a bare repository named `/opt/beta.git` (ensure exact name usage).


#### Solution:

* SSH into the storage server and install git using the command `sudo yum install git`
* Run this command to create a bare minimum repo `git init --bare /opt/beta.git`
