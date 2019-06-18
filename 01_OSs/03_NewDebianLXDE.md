a. Install base. Remove cdrom entries in sources:
```bash
vi /etc/apt/sources.list
```
b. Install LXDE minimal:
```bash
apt install lxde-core
```
c. Install unrar non-free as download, see: https://packages.debian.org/stretch/amd64/unrar/download

d. Apps optimization:
```bash
apt install -y lxterminal gdebi
apt autoremove -y termit lxtask nano xscreensaver
# or
apt purge xscreensaver lxlock
```
If preferences not saved make sure file exists and user owns:
```vim
~/.config/lxterminal
~/.config/lxterminal/lxterminal.conf
```
LXTerminal is a non-login shell. 
The start-up script is ~/.bashrc, not ~/.bash_profile or ~/.profile.

e. Browser install:
```bash
apt install slimjet # or download and gdebi slimjet_amd64.deb
```
f. Document viewer:
```bash
apt install -y qpdfview vim scite
```
g. Media support:
```bash
apt install -y mpv gthumb deluge k3b
```
h. Install file manager:
```bash
apt install -y mc
```
i. Install wine:
```bash
sudo dpkg --add-architecture i386 && sudo apt update
sudo apt install \
      wine \
      wine32 \
      wine64 \
      libwine \
      libwine:i386 \
      fonts-wine
```

k. Archive support:
```bash
apt-get install -y p7zip-full
```
l. Create desktop entries:
```vim
vi <shortcut>

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Icon=/home/tudi/Pictures/Hopstarter-Sleek-Xp-Basic-Folder.ico
Exec=pcmanfm -n "/media/tudi/system/01_ToRead/Go_Books (from vault)"
Name=Go
GenericName=Go
```
g. Enable numlock after boot. See: https://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen
```bash
sudo apt install numlockx
sudo vi /etc/lightdm/lightdm.conf
# add line:
greeter-setup-script=/usr/bin/numlockx on
```
