# Creating a Systemd Service for a Python Django Project on Ubuntu

## 1. Create a Systemd Service File

Create a new service file for your Django project. Open a terminal and use your preferred text editor to create the file. For example:


## Python Configure

```bash
sudo nano /etc/systemd/system/myproject.service

[Unit]
Description=Django API Service
After=network.target

[Service]
User=root
Group=root
WorkingDirectory=/repos/project/project_app
ExecStart=/repos/project/projectenv/bin/python /repos/project/project_app/manage.py runserver 0.0.0.0:8000
Restart=always

[Install]
WantedBy=multi-user.target

```
## java Configure

```bash
sudo nano /etc/systemd/system/myproject.service

[Unit]
Description=Spring Boot Application
After=syslog.target
[Service]
User=www-data
ExecStart=/usr/lib/jvm/java-17-openjdk-amd64/bin/java -jar /repos/project/target/project-SNAPSHOT.jar
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target

```

## 2. Reload Systemd
After creating the service file, reload Systemd to apply the changes:
```
sudo systemctl daemon-reload
```
## 3. Start and Enable the Service
```
sudo systemctl start myproject
sudo systemctl enable myproject
```
## 4. Check Service Status
```
sudo systemctl status myproject
```
## 4. Check Project Console
```
sudo journalctl -u myproject -f
```



