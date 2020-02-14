```html
https://www.ostechnix.com/install-oracle-virtualbox-ubuntu-16-04-headless-server/
```
#### Bring system to date
```bash
sudo apt update 
sudo apt upgrade
sudo apt dist-upgrade
```

sudo apt install build-essential dkms unzip
sudo reboot

#### Add Oracle VirtualBox official repository
sudo vi /etc/apt/sources.list
deb http://download.virtualbox.org/virtualbox/debian bionic contrib
deb http://download.virtualbox.org/virtualbox/debian stretch contrib

#### Add the Oracle public key
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

#### Install
sudo apt update
sudo apt install virtualbox-5.2

#### Add user to vboxusers group
```bash
sudo usermod -aG vboxusers <user>
```

check status: 
sudo systemctl status vboxdrv

6. download the latest Extension pack for VirtualBox 5.2.x
wget https://download.virtualbox.org/virtualbox/5.2.14/Oracle_VM_VirtualBox_Extension_Pack-5.2.14.vbox-extpack

now install:
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-5.2.14.vbox-extpack

#### For headless servers install phpVirtualBox:
a. get prerequisites
```bash
sudo apt install apache2 php php-mysql libapache2-mod-php php-soap php-xml
```
b. download
```
wget https://github.com/phpvirtualbox/phpvirtualbox/archive/5.2-0.zip
```
c. unzip
unzip 5.2-0.zip

d. move to apache folder
sudo mv phpvirtualbox-5.2-0/ /var/www/html/phpvirtualbox
sudo chmod 777 /var/www/html/phpvirtualbox/

e. configure phpVirtualBox
sudo cp /var/www/html/phpvirtualbox/config.php-example /var/www/html/phpvirtualbox/config.php

sudo vi /var/www/html/phpvirtualbox/config.php

configure user credentials:
var $username = '<user>';
var $password = '<password>';

create new file:
sudo vi /etc/default/virtualbox

add to file: VBOXWEB_USER=<user>

f. restart services for new configuration to be loaded:
sudo systemctl restart vboxweb-service
sudo systemctl restart vboxdrv
sudo systemctl restart apache2

g. login with admin/admin
ip/phpvirtualbox

8. linux mint 19 xfce install
a. on connecting host:
sudo apt install rdesktop
rdesktop -a 16 -N 192.168.1.x:9000

b. not sure, might work without:
sudo apt-get install virtualbox-guest-utils
sudo apt-get install virtualbox-guest-dkms

vboxmanage setextradata mint GUI/LastGuestSizeHint 1920,1080

c. start mint in compatibility mode from start menu
