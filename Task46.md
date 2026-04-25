### Task:

The Nautilus Application
development team recently finished development of one of the apps that
they want to deploy on a containerized platform. The Nautilus
Application development and DevOps teams met to discuss some of the
basic pre-requisites and requirements to complete the deployment. The
team wants to test the deployment on one of the app servers before going
 live and set up a complete containerized stack using a docker compose
fie. Below are the details of the task:

1. On `App Server 2` in `Stratos Datacenter` create a docker compose file `/opt/security/docker-compose.yml` (should be named exactly).
2. The compose should deploy two services (web and DB), and each service should deploy a container as per details below:

`For web service:`

a. Container name must be `php_host`.

b. Use image `php` with any `apache` tag. Check [here](https://hub.docker.com/_/php?tab=tags/) for more details.

c. Map `php_host` container's port `80` with host port `5003`

d. Map `php_host` container's `/var/www/html` volume with host volume `/var/www/html`.

`For DB service:`

a. Container name must be `mysql_host`.

b. Use image `mariadb` with any tag (preferably `latest`). Check [here](https://hub.docker.com/_/mariadb?tab=tags/) for more details.

c. Map `mysql_host` container's port `3306` with host port `3306`

d. Map `mysql_host` container's `/var/lib/mysql` volume with host volume `/var/lib/mysql`.

e. Set MYSQL_DATABASE=`database_host` and use any custom user ( except root ) with some complex password for DB connections.

3. After running docker-compose up you can access the app with curl command `curl <server-ip or hostname>:5003/`

For more details check [here](https://hub.docker.com/_/mariadb?tab=description/).


#### Solution:

```
version: '3.8'

services:
  web:
    container_name: php_host
    image: php:apache
    ports:
      - "5003:80"
    volumes:
      - /var/www/html:/var/www/html
    depends_on:
      - db

  db:
    container_name: mysql_host
    image: mariadb:latest
    ports:
      - "3306:3306"
    volumes:
      - /var/lib/mysql:/var/lib/mysql
    environment:
      MYSQL_DATABASE: database_host
      MYSQL_USER: app_user
      MYSQL_PASSWORD: Str0ng!Passw0rd123
      MYSQL_ROOT_PASSWORD: RootStr0ng!Passw0rd456

```

and run this command

```
docker compose -f /opt/security/docker-compose.yml up -d
```
