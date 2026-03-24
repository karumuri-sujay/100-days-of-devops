### Task:

1. Install and configure `nginx` on `App Server 2`.
2. On `App Server 2` there is a self signed SSL certificate and key present at location `/tmp/nautilus.crt` and `/tmp/nautilus.key`. Move them to some appropriate location and deploy the same in Nginx.
3. Create an `index.html` file with content `Welcome!` under Nginx document root.
4. For final testing try to access the `App Server 2` link (via hostname) from `jump host` using curl command. For example: `curl -Ik https://<app-server-name>/`.


#### Solution:

* Install nginx using the command `sudo dnf install nginx -y`
* Move the certs to the location `/etc/certs`.
  * `sudo mkdir -p /etc/certs`
  * `sudo cp /tmp/nautilus.* /etc/certs`
* Index.html is in the location `/etc/share/nginx/html/index.html`. Change the content using the command `echo Welcome! > /etc/share/nginx/html/index.html`
* Go to the location `/etc/nginx/nginx.conf` and uncomment the server code. Also update these lines to use the given private cert and key. `ssl_certificate "/etc/certs/nautilus.crt"; ssl_certificate_key "/etc/certs/nautilus.key";`
* Enable and start the nginx service using the systemctl command.
