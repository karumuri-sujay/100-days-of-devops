### Task:

a. Install/Configure MariaDB server.

b. Create a database named `kodekloud_db1`.

c. Create a user called `kodekloud_tim` and set its password to `BruCStnMT5`.

d. Grant full permissions to user `kodekloud_tim` on database `kodekloud_db1`.

#### Solution:

* Install MariaDB server using the command `sudo dnf install maria mariadb-server`
* Enable and start the service using the systemctl command
* Go inside of mysql and enter the below set of commands
  * `CREATE DATABASE kodekloud_db1;`
  * `CREATE USER 'kodekloud_pop'@'localhost' IDENTIFIED BY 'dCV3szSGNA';`
  * `GRANT ALL PRIVILEGES ON kodekloud_db6.* TO 'kodekloud_pop'@'localhost';`
