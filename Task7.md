### Task:

Password-less authentication to app servers


#### Solution:

1. Generate RSA key using the command `ssh-keygen -t rsa 2048 -b `.
2. The key will be stored in the `~/id_rsa.pub`
3. Use the package `ssh-copy-id` to copy the key of the current server to the app servers
4. The command goes as `ssh-copy-id tony@stapp01`
