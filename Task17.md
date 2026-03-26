### Task:

a. Create a database user `kodekloud_tim` and set its password to `8FmzjvFU6S`.

b. Create a database `kodekloud_db7` and grant full permissions to user `kodekloud_tim` on this database.

#### Solution:

* SSH into database server
* Enter the command `sudo -u postgres psql` to go inside of SQL
* Create user with command `CREATE USER kodekloud_tim WITH ENCRYPTED PASSWORD '8FmzjvFU6S';`
* Create DB with command `CREATE DATABASE kodekloud_db7;`
* Grant permissions using `GRANT ALL PRIVILEGES ON DATABASE kodekloud_db7 to kodekloud_tim;`
