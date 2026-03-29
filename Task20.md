### Task:

a. Install `nginx` on `app server 3` , configure it to use port `8095` and its document root should be `/var/www/html`.

b. Install `php-fpm` version `8.3` on `app server 3`, it must use the unix socket `/var/run/php-fpm/default.sock` (create the parent directories if don't exist).

c. Configure php-fpm and nginx to work together.

d. Once configured correctly, you can test the website using `curl http://stapp03:8095/index.php` command from jump host.


#### Solution:

Run these commands

```
sudo dnf install nginx -y
sudo dnf module install php:8.3 -y

sudo mkdir -p /var/run/php-fpm
sudo vi /etc/php-fpm.d/www.conf

listen = /run/php-fpm/www.sock update this line with expected directory. It should be listen = /var/run/php-fpm/default.sock

sudo vi /etc/nginx/nginx.conf
#change port 80 to 8085
#change root to /var/www/html

sudo vi /etc/nginx/default.d/php.conf
Update fastcgi_pass php-fpm; to this: fastcgi_pass unix:/var/run/php-fpm/default.sock;

sudo systemctl enable --now nginx
sudo systemctl enable --now php-fpm
```
