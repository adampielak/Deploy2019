##### a. Install base. Remove cdrom entries in sources:
```bash
vi /etc/apt/sources.list
```
##### b. Install LXDE minimal:
```bash
apt install lxde-core
```
##### c. Apps optimization:
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

##### d. Browser install:
```bash
# Firefox install:
apt-get install firefox-esr
# Download Slimjet and install as non root
vi /etc/sudoers
sudo gdebi slimjet_amd64.deb
```
##### e. Document viewer:
```bash
apt install -y qpdfview vim scite
```
##### f. Media support:
```bash
apt install -y mpv nomacs deluge qbittorrent xfburn soundconverter
```
Sound converter
```html
https://soundconverter.org/
```
Torrent client:
```html
qbittorrent.org
```
##### g. Install file manager:
```bash
apt install -y mc
```
Or krusader (with KRename)
```html
https://krusader.org/
```
##### h. Install wine:
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
##### k. Archive support:
```bash
apt-get install -y p7zip-full
wget https://www.rarlab.com/rar/rarlinux-x64-5.7.1.tar.gz
```
Add rar path to PATH in $HOME/bashrc
##### l. Create desktop entries:
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
##### m. Enable numlock after boot. 
See:
```html
https://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen
```
```bash
sudo apt install numlockx
sudo vi /etc/lightdm/lightdm.conf
# add line:
greeter-setup-script=/usr/bin/numlockx on
```
