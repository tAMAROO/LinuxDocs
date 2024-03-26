###   WebStack Install

Hypervisor:
======
##  Install Proxmox:
1. Visit https://www.proxmox.com/en/downloads - and grab the latest version of Proxmox Virtual Environment.
2. Use Rufus to make bootable USB.
3. Use default values through whole installation of PVE.
4. Boot PVE.
5. Once logged into PVE web console create four VM's.  Load the VM's with Ubuntu Server 22.04 LTS https://ubuntu.com/download/server
   - DNS
   - WEB
   - WIKI
   - FS
6. After server OS is installed run the following:
   - sudo apt update & sudo apt upgrade
   - sudo ufw enable
   - sudo ufw allow 'OpenSSH'
     
LAMP Server:
======

##  Install Apache:
1. ```sudo apt install apache2```
2. ```sudo systemctl status apache2```
3. ```sudo systemctl enable --now apache2```
4. ```sudo ufw allow 'Apache'```
5. ```Check Apache is working: http://server-ip```

##  Install MariaDB:
1. ```sudo apt install mariadb-server```
2. ```sudo systemctl status  mariadb```
3. ```sudo systemctl enable mariadb```
4. ```sudo mysql_secure_installation'```
 - Hit <b>Enter</b>
 - Change Root Password = <b>N</b>
 - Remove anonymous users = <b>Y</b>
 - Disallow remote root login = <b>Y</b>
 - Remove test database = <b>Y</b>
 - Reload privilege tables = <b>Y</b>

##  Install PHP:
 1. ```sudo apt install php8.1 libapache2-mod-php8.1```
 2. ```php -v```
 3. ```echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php```
 4. ```check php is installed correctly: http://server-ip/info.php'```
    - <b>Optional</b>
     - ```sudo apt install  php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-intl -y```
   
##  LAMP Server Configurations:
- Allow FTP access:
   - ```sudo ufw allow 22```
   - ```groupadd <b>groupname</b>```
   - ```usermod -a -G <b>groupname</b> <b>user</b>```
   - ```sudo chown -R :<b>groupname</b> /var/www```
   - ```sudo chmod -R g+rw /var/www```
- Set up Default facing page:
   - ```cd /etc/apache2/mods-available/```
   - ```sudo nano dir.conf```
   - Add <b>pageyouwant.html</b> to the front of text in front of index.html.
