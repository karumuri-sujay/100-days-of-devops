### Task:

Disable direct root login via SSH on all application servers to enhance security. This fundamental security hardening practice prevents attackers from directly targeting the root account and enforces the use of individual user accounts with sudo privileges for administrative tasks.


### Solution:

1. SSH into the server
2. Disable root login by mentioning `PermitRootLogin` to "NO". Use this command

   `sudo sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config`
3. Restart the sshd service and check the status

   ```
   sudo systemctl status sshd
   sudo systemctl restart sshd
   ```
