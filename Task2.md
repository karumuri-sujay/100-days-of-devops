### Task:

Establish a time-limited user account with automatic expiration. This approach supports temporary project assignments by ensuring accounts become inactive after a specified date without manual intervention.


### Solution:

1. SSH into the server stapp01

   `ssh <user-name>@<ip-addr>`
2. Create user with the expiration date mentioned

   `sudo useradd -e <expiry-date> <user-name>`
3. Verify whether the user is created or not in `/etc/passwd`


##### References:

https://kodekloudhub.github.io/kodekloud-engineer/docs/projects/nautilus#infrastructure-details
