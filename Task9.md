### Task:

There is a critical issue going on with the `Nautilus` application in `Stratos DC`. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.

Look into the issue and fix the same.


#### Solution

1. ssh into the server stdb01
2. Check the status of mariadb using the command `sudo systemctl status mariadb`
   1. Shows disabled
3. Enable and start the mariadb service using the command `sudo systemctl enable mariadb ` and `sudo systemctl start mariadb`
4. Check the status now
   1. Shows service is enabled and preset is disabled
   2. Check the logs below
5. Useful log is `chown: changing ownership of '/var/lib/mysql': Operation not permitted`
6. Check the permissions of the file in that location using the command `ls -al`
7. Update the permissions to `mysql:mysql` using the command `sudo chown mysql:mysql /var/lib/mysql`
8. Make the file executable using the command `sudo chmod 755 /var/lib/mysql`
9. Restart the mariadb service using the command `sudo systemctl restart mariadb`
10. Verify the status of mariadb after a minute -> service will be enabled
11. You can also check with the command `mysql` to verify if the sql server is working or not.
