### Task:

a. Install `httpd` package and dependencies on `app server 1`.

b. Apache should serve on port `6000`.

c. There are two website's backups `/home/thor/blog` and `/home/thor/demo` on `jump_host`. Set them up on Apache in a way that `blog` should work on the link `http://localhost:6000/blog/` and `demo` should work on link `http://localhost:6000/demo/` on the mentioned app server.

d. Once configured you should be able to access the website using `curl` command on the respective app server, i.e `curl http://localhost:6000/blog/` and `curl http://localhost:6000/demo/`

#### Solution:

* Install httpd service using the command `yum install httpd -y`
* Edit the configuration file for the apache server in the location `/etc/httpd/conf/httpd.conf` and update the port from 80 to 6000
* Use SCP to copy the file from jump-host server to app-server
* Move the /blog and /demo folders to `/var/www/html` location
* Start the service using systemctl command.
* Verify using curl commands
