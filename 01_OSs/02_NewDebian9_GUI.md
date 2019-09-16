##### Download disc 1:
```bash
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-9.6.0-amd64-xfce-CD-1.iso
sudo vi /etc/apt/sources.list
```
Mandatory set mirror - mirror would enable all options for install. Check only system utilities and ssh server.

##### Run as root:
```bash
apt install lxqt
```
##### Prerequisites:
```bash
apt install -y sudo vim
```
##### Vim customization
```bash
vi .vimrc  # for user and root (sudo), add:
```
```vim
colo desert
set number
```
##### Install wine:
```bash
sudo dpkg --add-architecture i386 && sudo apt update
sudo apt install wine wine32 wine64 libwine libwine:i386 fonts-wine
```
##### Install X11:
```bash
apt install -y lxqt-core lxqt # LXQT
apt install -y lxde-core      # LXDE
```
##### Check services per run level
```bash
ls /etc/rc*.d
```
