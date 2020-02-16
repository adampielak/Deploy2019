## Buster 10.3 -  Virtual Box 6.1
### Headless Install
```bash
su -
apt install build-essential dkms unzip wget
wget https://download.virtualbox.org/virtualbox/6.1.2/virtualbox-6.1_6.1.2-135662~Debian~buster_amd64.deb
gdebi virtualbox-6.1_6.1.2-135662~Debian~buster_amd64.deb 
```
#### Check service status
```bash
 systemctl status vboxdrv
 ```
### Install Extension Pack
Extension Pack is needed for Remote Display.
```bash
wget https://download.virtualbox.org/virtualbox/6.1.2/Oracle_VM_VirtualBox_Extension_Pack-6.1.2.vbox-extpack
```
Install.
 ```bash
VBoxManage extpack install <pack>
```
Install rdesktop on host used for management.
```bash
apt install rdesktop
# to connect: rdesktop -a 16 -N 192.168.1.x:3389
```
### Install phpvirtualbox
 ```bash
apt install apache2 php php-mysql libapache2-mod-php php-soap php-xml
 ```
Download
```bash
wget https://github.com/phpvirtualbox/phpvirtualbox/archive/develop.zip
```
Unzip
```bash
unzip 5.2-1.zip
```
Move to Apache folder
```bash
mv phpvirtualbox-5.2-1/ /var/www/html/phpvirtualbox
```
Copy configuration
```bash
cp /var/www/html/phpvirtualbox/config.php-example /var/www/html/phpvirtualbox/config.php
```
Set user owing VB process
```bash
vi /var/www/html/phpvirtualbox/config.php
# edit var $username = 'user';
# edit var $password = 'pass';
```
Create VB file
```bash
vi /etc/default/virtualbox
# add line with previously used user VBOXWEB_USER=user
```
Reboot.
### Connect
Login with admin/admin at ip/phpvirtualbox.
