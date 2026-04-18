### Task:

One of the Nautilus DevOps team members was working to configure services on a `kkloud` container that is running on `App Server 3` in `Stratos Datacenter`.
 Due to some personal work he is on PTO for the rest of the week, but we
 need to finish his pending work ASAP. Please complete the remaining
work as per details given below:

a. Install `apache2` in `kkloud` container using `apt` that is running on  `App Server 3` in `Stratos Datacenter`.

b. Configure Apache to listen on port `3002` instead of default `http`
 port. Do not bind it to listen on specific IP or hostname only, i.e it
should listen on localhost, 127.0.0.1, container ip, etc.

c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

#### Solution:

SSH into the app server and these commands

```
docker exec -it 90ea27b7a9bd apt install apache2

docker exec -it 90ea27b7a9bd sudo sed -i 's/Listen 80/Listen 3002/' /etc/apache2/ports.conf <!-updating port->
docker exec -it 90ea27b7a9bd sh -c 'echo "ServerName localhost" >> /etc/apache2/apache2.conf'

docker exec -it 90ea27b7a9bd service apache2 start

```
