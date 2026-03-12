### Task:

Install and configure the cron service on all Nautilus application servers, then create a scheduled job for automated task execution. This establishes the foundation for automated system maintenance, monitoring, and operational tasks across the infrastructure.


### Solution:

1. SSH into the server
2. Enter into root user using `sudo -i`
3. Install cronie packages using the command - `sudo dnf install -y cronie`
4. Start the crond service with the command `sudo systemctl start crond`
5. To start a cron job, use the command `sudo crontab -l`
6. Enter the crob job given and save.
7. To know whether the cronjob is created or not, use this command `sudo crontab -e`
