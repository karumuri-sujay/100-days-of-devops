### Task:


The monitoring tool has reported an issue in Stratos Datacenter. One of the app servers has a problem where its Apache service is not reachable on port 3000 (which is the configured Apache port). The service itself could be down, the firewall could be at fault, or something else could be causing the issue.

**Objectives:**

1. Use diagnostic tools (telnet, netstat, etc.) to identify the root cause
2. Fix the issue without compromising security settings
3. Ensure Apache is reachable from the jump host
4. Test accessibility using: `curl http://stapp01:3000`

#### Solution:

* Check the httpd service using command `sudo systemctl status httpd`
  * Status will be disabled
* Verify if any other service is running on port 3000 using ss command `sudo ss -tlnup | grep 3000`
* Edit the file /etc/mail/sendmail.mc and update the DAEMON_PORT to other port (ex:1234)
* Restart the service using the command `sudo systemctl restart sendmail`
  * Service should be running
  * You can use the above ss command with port 1234 to check if the port is running as expected
* Now restart the httpd service `sudo systemctl restart httpd`
  * Status should be in running
* From the jump host server, verify the connection using the command `curl http:stapp01:3000`
  * Output should be in html.
