### Task:

We have one of our websites up and running on our Nautilus infrastructure in Stratos DC. Our security team has raised a concern that right now Apache’s port i.e `6200` is open for all since there is no firewall installed on these hosts. So we have decided to add some security layer for these hosts and after discussions and recommendations we have come up with the following requirements:

1. Install `iptables` and all its dependencies on each app host.
2. Block incoming port 8083 on all apps for everyone except for `LBR` host.
3. Make sure the rules remain, even after system reboot.

#### Solution:

* SSH into the LBR host and check the **public ip address** using the command `ip addr`
* Install iptables using the command `sudo dnf install iptables iptables-services -y`
* Enable the port 8083 using the command `sudo iptables -A INPUT -p tcp --dport 5004 -s 10.244.234.212 -j ACCEPT`
* To reject other ports, run this command `sudo iptables -A INPUT -p tcp --dport 5004 -j REJECT`
* To save the rules, run this command `sudo iptables-save > /etc/sysconfig/iptables`
* Enable and start the service using the systemctl command
