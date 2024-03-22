### Setting Up SFTP on Ubuntu VPS

1. **Connect to your VPS via SSH:**
```bash
   ssh username@server_ip
```
### Create a new user for SFTP:
```
sudo adduser newusername
```
### Edit SSH configuration file:
```
sudo nano /etc/ssh/sshd_config
```
### Uncomment the following lines to allow root login and SFTP:
```
PermitRootLogin yes
Subsystem sftp /usr/lib/openssh/sftp-server
```
### Set password for the new user:
```
sudo passwd newusername
```
### Optionally, set a password for the root user:
```
sudo passwd root
```
### Restart SSH service to apply changes:
```
sudo service ssh restart
```
### Accessing SFTP
Once you have completed these steps, you should be able to connect to your VPS using SFTP using the new username and password.