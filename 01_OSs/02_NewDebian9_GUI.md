## Contents <a name="contents"></a>
* [Download ISO](#download)
* [Install Windows Manager](#lxqt)
* [VIM Customization](#vim)
* [WINE](#wine)
* [Check Running Services](#check)

### Download <a name="download"></a>
```bash
wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-9.6.0-amd64-xfce-CD-1.iso
sudo vi /etc/apt/sources.list
```
Mandatory set mirror - mirror would enable all options for install. Check only system utilities and ssh server.

### Install Windows Manager <a name="lxqt"></a>
```bash
apt install lxqt
# or for minimal
apt install -y lxqt-core      # LXQT
apt install -y lxde-core      # LXDE
```
### VIM <a name="vim"></a>
```bash
apt install -y sudo vim
vi .vimrc  
# for user and root (sudo), add:
colo desert
set number
```
### WINE <a name="wine"></a>
```bash
sudo dpkg --add-architecture i386 && sudo apt update
sudo apt install wine wine32 wine64 libwine libwine:i386 fonts-wine
```
### Check services per run level <a name="check"></a>
```bash
ls /etc/rc*.d
```
