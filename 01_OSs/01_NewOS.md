USB maker:
https://www.balena.io/etcher/
download and run the AppImage with sudo.
```bash
sudo gparted  //delete any partitions on stick
```

#### 1. TeamViewer
```html
https://www.teamviewer.com/en/download/linux/
```

#### 2. Change timezone:
```bash
sudo timedatectl set-timezone Europe/Bucharest
```

#### 3. Git
prerequisites: 
```bash
sudo apt-get install build-essential
sudo apt-get update
sudo apt-get install git
```
#### 4. Firefox optimization and bookmarks
SSD optimization:
about:config
browser.cache.disk.enable - set to false

browser.sessionstore.interval - set to 3600000. or one hour

create key for memory cache, right click with type integer:
disk.cache.memory.capacity
131072 for 128 Mb. value in KB

#### 5. RAM Disk
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
#### 6. SSH Key
```bash
ssh-keygen -t rsa -C "your.email@example.com" -b 4096
xclip -sel clip < ~/.ssh/id_rsa.pub
```
#### 7.VLC
```html
https://community.linuxmint.com/software/view/vlc
```
*if no image but sound change the video output to X11

mpeg 4 AAC codec for burner: sudo apt-get install gstreamer1.0-libav

#### 8.JavaScript Editor
http://brackets.io/
https://code.visualstudio.com/

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

#### 9.Disk burner:
K3b - Disk Burning

#### 10.wine:
```bash
sudo apt update
sudo apt-get install wine wine32 wine-stable
```
#### 11.Mikrotik Winbox:
```bash
wget http://www.mikrotik.com/download/winbox.exe
wine winbox.exe
```
alternative for finding IPs on LAN:
```bash
nmap -sP 192.168.1.0-45
```
#### 12. SlimJet browser for default browsing.
```bash
sudo apt install slimjet
```
Set cache for for RAM disk.

#### 13. Midnight Commander
```bash
sudo apt install mc
```
#### 14. 7zip
```bash
sudo apt-get install p7zip-full p7zip-rar
```
convert to mp3:
```bash
ffmpeg -i file.mp4 -b:a 192k file.mp3
```
#### 15. Remote Desktop like:
server:
```html
https://wiki.x2go.org/doku.php/doc:installation:x2goserver
```
connecting client:
```html
https://wiki.x2go.org/doku.php/doc:installation:x2goclient
```
#### 16. Color picker:  
```bash
sudo apt-get install gpick
```
#### 17. QPDF for PDF documents.
#### 18. Screen capture:
http://shutter-project.org/downloads/
```bash
sudo add-apt-repository ppa:shutter/ppa
sudo apt-get update && sudo apt-get install shutter
```
remove:
```bash
sudo rm /etc/apt/sources.list.d/ppa_shutter_ppa_tara.list
```
#### 19. Photo Viewer
```bash
sudo apt-get install gthumb
```
#### 20. VirtualBox
```bash
sudo apt-get install dkms
wget http://download.virtualbox.org/virtualbox/5.2.14/virtualbox-5.2_5.2.14-123301~Ubuntu~bionic_amd64.deb
```
start headless:
```bash
vboxheadless --startvm <name>
```
#### 21. LibreOffice
```bash
sudo apt-add-repository ppa:libreoffice/ppa
sudo apt update
sudo apt-get install libreoffice
# or
sudo apt-get install libreoffice-writer
# or
sudo apt-get install libreoffice-calc
```
#### 22. Calculator
```bash
sudo apt install galculator
```
