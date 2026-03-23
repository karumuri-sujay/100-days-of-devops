### Task:

The production support team of xFusionCorp Industries has deployed some of the latest monitoring tools to keep an eye on every service, application, etc. running on the systems. One of the monitoring systems reported about Apache service unavailability on one of the app servers in `Stratos DC`.

Identify the faulty app host and fix the issue. Make sure Apache service is up and running on all app hosts. They might not have hosted any code yet on these servers, so you don't need to worry if Apache isn't serving any pages. Just make sure the service is up and running. Also, make sure Apache is running on port `8089` on all app servers.


#### Solution:

* SSH into app servers and compare the processes between them using the command `ps aux`
  * In one of the servers, apache will not be in running state
* On the fault server, check which service is being running on port 8089 using the command `sudo lsof -i:8089`
  * In my case, the running service on this port is sendmail
* From the command `sudo systemctl status sendmail`, find the process-id and kill the process using the command `sudo kill -9 <PID>`
* Restart the httpd service using the command `sudo systemctl restart httpd`
* Verify whether the apache server is running or not using the first command.
