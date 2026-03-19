### Task:

* Install Tomcat on App Server 2 (hostname: `stapp02`).
* Configure Tomcat to listen on port `5000`.
* Deploy the `ROOT.war` located on the Jump host at `/tmp/ROOT.war` so the app is available directly at `http://stapp02:5000`.


#### Solution:

* Verify whether the java is installed or not using `where java`.
  1. Copy the location of the java
* Add a user with tomcat using the command `sudo groupadd tomcat`
  * `sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat`
* Install tomcat using wget `wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz`
* Extract the output with the command `sudo tar -xf apache-tomcat-9.0.80.tar.gz -C /opt/tomcat --strip-components=1`
  1. Check strip-components does
* Provide permissions using the commands

```
sudo chown -R tomcat:tomcat /opt/tomcat
sudo chmod -R u+rX /opt/tomcat
```

* Go inside of this file `vi /opt/tomcat/conf/server.xml` and update the CONNECTOR PORT to 8087 (given in the question)
* From the jump host server, transfer the file `sudo cp /tmp/ROOT.war /opt/tomcat/webapps/`
* Provide tomcat permissions to the file
* Run these commands

  ```
  sudo tee /etc/systemd/system/tomcat.service > /dev/null <<'EOF'
  [Unit]
  Des

  cription=Apache Tomcat Web Application Container
  After=network.target

  [Service]
  Type=forking
  User=tomcat
  Group=tomcat
  Environment=JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.20.1.1-2.el9.x86_64
  Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid
  Environment=CATALINA_HOME=/opt/tomcat
  Environment=CATALINA_BASE=/opt/tomcat
  ExecStart=/opt/tomcat/bin/startup.sh
  ExecStop=/opt/tomcat/bin/shutdown.sh
  Restart=on-failure

  [Install]
  WantedBy=multi-user.target
  EOF
  ```
* Run these commands to reload systemctl to identify tomcat

  ```
  sudo systemctl daemon-reload
  sudo systemctl enable tomcat
  sudo systemctl start tomcat
  sudo systemctl status tomcat
  ```
* Start the tomcat with the command `sudo -u tomcat /opt/tomcat/bin/startup.sh`
* Verify whether the port is opened or not using the command `curl http://stapp03:8087`


####References
https://github.com/kodekloudhub/100-days-of-devops/blob/main/tasks/week-02/day-11.md
