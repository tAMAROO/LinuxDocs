# SSH

##  1. Change SSH Port Number:

##### Info:

|Port Category|Range|Usage|
| ------------- |:-------------:| -------:|
| Well known/System Ports | 0 -1023 |These are reserved ports for running system-specific services like SSH which usually runs on 22, HTTPS listens on 443, etc and the process must execute with superuser privileges to be able to bind a network socket to an IP address using one of the well-known ports. |
| Registered Ports      | 1024 – 49151 |These ports are assigned by IANA for specific services upon application by a requesting entity and they can also be used by ordinary users. |
| Dynamic/Private ports | 49152 -65535 |These ports cannot be registered with IANA, it is used for private or customized services or for temporary purposes.|

1. Choose a port.
2. Check if port is open:
   ```$ sudo lsof -i -P -n | grep LISTEN | grep <port>```
3. Once you have found an open port you will need to edit the sshd_config file.  This file should be found in /etc/ssh.  Or you can search for it in terminal:
   ```$ find /etc -name sshd_config```
4. In sshd_config find the commented line that reads ```#Port 22```.  Uncomment this line and change "22" to the port that you chose earlier.
5. Restart the sshd service:
   ```$ sudo systemctl restart sshd```

##  2. Open SSH in the Firewall:

1. Open the port you chose in the firewall:
   ```$ sudo firewall-cmd --permanent --zone="zone" --add-port=xxxx```
   ```$ sudo firewall-cmd --reload```

## Research assets:

URL: https://www.geeksforgeeks.org/how-to-change-the-default-ssh-port-in-linux/

URL: https://firewalld.org/documentation/howto/open-a-port-or-service.html
