### Task:

Your task is to grant executable permissions to the `/tmp/xfusioncorp.sh` script on `App Server 3`. Additionally, ensure that all users have the capability to execute it.


#### Solution:

1. SSH to the server
2. Update the permissions to executable

   `sudo chmod 777 /tmp/xfusioncorp.sh`
3. Check whether the permissions is updated with the command

   `ls -ltr /tmp/xfusioncorp.sh`
