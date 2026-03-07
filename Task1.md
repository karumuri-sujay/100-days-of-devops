### Task:

Configure a system user account with shell access disabled. This type of account serves automation workflows and service operations that don't need interactive terminal sessions.


### Solution:

1. Login into the server using ssh

   `ssh <user-name>@<ip-address>`
2. Create a user with nologin permissions using useradd command.

   `sudo useradd -m -s /usr/sbin/nologin user-name`

   - -s is for non-interactive shell permissions
3. Verify whether the user is created or not in the `etc/passwd`.

##### References:

https://kodekloudhub.github.io/kodekloud-engineer/docs/projects/nautilus#infrastructure-details
