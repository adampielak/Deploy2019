# Debian: OS Optimizations <a name="top"></a>
* [Date and Time](#time)
* [RAM and Disk](#ram)
* [SSH](#ssh)
* [File Management](#file)
* [Comms](#comms)
* [Media](#media)
* [Office](#office)
* [Development](#dev)

## Date and Time <a name="time"></a> 
### Change timezone:
```bash
sudo timedatectl set-timezone Europe/Bucharest
```

## RAM and Disk <a name="ram"></a> ([Up](#top))
### RAM Disk
```bash
sudo mkdir /mnt/tmpfs.ramdisk
sudo vi /etc/fstab
tmpfs   /mnt/tmpfs.ramdisk  tmpfs  nodev,nosuid,nodiratime,size=100M 0  0
ln -s /mnt/tmpfs.ramdisk $HOME/ram
```
Make terminal shortcut open in RAM disk:
```bash
xfce4-terminal --default-working-directory=/home/user/ram
```
### Disable swap
```bash
sudo swapoff -a
```
Permanent
```bash
vi /etc/fstab
# add /swap.img      none    swap    sw      0       0
```
## SSH <a name="ssh"></a> ([Up](#top))
```bash
ssh-keygen -t rsa -C "your.email@example.com" -b 4096
xclip -sel clip < ~/.ssh/id_rsa.pub
```

## File Management <a name="file"></a> ([Up](#top))
### Midnight Commander
```bash
sudo apt install mc
```
### 7zip
```bash
sudo apt-get install p7zip-full p7zip-rar
```
### RAR
```bash
wget https://www.rarlab.com/rar/rarlinux-x64-5.7.1.tar.gz
```
Add rar path to PATH in $HOME/bashrc.
### Torrent Client
```bash
sudo apt install qbittorrent
```
### Disk burner XFBurn
```html
http://www.xfce.org/projects/xfburn
```
### QPDF
```html
https://launchpad.net/qpdfview
```
### wine
```bash
sudo apt update
sudo apt-get install wine wine32 wine-stable
```
or
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

## Comms <a name="comms"></a> ([Up](#top))
### USB Tethering
```bash
apt install network-manager
```
### SlimJet browser
```bash
sudo apt install slimjet  # if not work download and install as non root
sudo gdebi slimjet_amd64.deb
```
Set cache for for RAM disk.
### Firefox ESR
```bash
apt-get install firefox-esr
```
### TeamViewer
```html
https://www.teamviewer.com/en/download/linux/
```
### Remote Desktop like (under review)
server:
```html
https://wiki.x2go.org/doku.php/doc:installation:x2goserver
```
connecting client:
```html
https://wiki.x2go.org/doku.php/doc:installation:x2goclient
```
### Mikrotik Winbox
```bash
wget http://www.mikrotik.com/download/winbox.exe
wine winbox.exe
```
alternative for finding IPs on LAN:
```bash
nmap -sP 192.168.1.0-45
```

## Media <a name="media"></a> ([Up](#top))
### VLC
```html
https://community.linuxmint.com/software/view/vlc
```
*if no image but sound change the video output to X11 <br/>
mpeg 4 AAC codec for burner: sudo apt-get install gstreamer1.0-libav
### Color picker 
```bash
sudo apt-get install gpick
```
### Photo Viewer
```html
https://nomacs.org
```
### Screen capture
http://shutter-project.org/downloads/
```bash
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update && sudo apt-get install shutter
```
remove:
```bash
sudo rm /etc/apt/sources.list.d/ppa_shutter_ppa_tara.list
```
### Sound converter
```html
https://soundconverter.org/
```

## Office <a name="office"></a> ([Up](#top))
### Enable numlock after boot 
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
### Keyboard shortcuts
```bash
vi ~/.bash_aliases
# add:
alias r2='rm -rf *'
```
Load new entries with bash or open new terminal window.
### Calculator
```bash
sudo apt install galculator
```
### LibreOffice
Prerequisites:
```bash
sudo apt-get install -y software-properties-common
```
```bash
sudo apt-add-repository ppa:libreoffice/ppa
sudo apt update
sudo apt-get install libreoffice
# or
sudo apt-get install libreoffice-writer
# or
sudo apt-get install libreoffice-calc
# or
sudo apt-get install libreoffice-impress
```

## Development <a name="dev"></a> ([Up](#top))
### Git
Prerequisites: 
```bash
sudo apt-get install build-essential
sudo apt-get update
sudo apt-get install git
# or
sudo apt install git-all
```
For GIT credential stores check: 
```html
https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage
```
### Markdown Editor
```html
http://pad.haroopress.com/
```
### Brackets Editor
http://brackets.io/

Brackets
for plugins: https://www.webpagefx.com/blog/web-design/brackets-extensions/
for SCSS: http://harikrishkk.blogspot.ro/2016/01/brackets-sass-plugin-setup.html
1. install plugin 'Brackets SASS', 'Minimap', 'Emmet'
2. touch .brackets.json in root folder. mkdir scss. create scss file. might consider doing a backup of css file.
3. add to it:
```css
{
    "sass.enabled": false,
    "sass.compiler": "libsass",
    "path": {
        "scss/style.scss": {
            "sass.enabled": true, 
            "sass.options": {                
                "outputDir": "../css/",
                "imagePath": null,
                "sourceComments": false,
                "outputStyle": "nested"
            },
            "linting.collapsed": true
        }
    }
}
```

test with:
```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="css/styles.css">
</head>

<body>
    <p>This is a test.</p>
</body>
</html>
```
and:
```css
$blue: #4000FF;

body {
    background-color: $blue;
}
```
First time to trigger the compilation update the scss file. This should trigger the transpiler.

### Geany IDE
For fast file viewing.

### VirtualBox
```bash
sudo apt-get install dkms
wget http://download.virtualbox.org/virtualbox/5.2.14/virtualbox-5.2_5.2.14-123301~Ubuntu~bionic_amd64.deb
```
start headless:
```bash
vboxheadless --startvm <name>
```
