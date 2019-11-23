#### GIT install
```bash
sudo apt-get install git
```
In order to be able to use go get -v with private repos:
```bash
git config --global --add url."git@github.com:".insteadOf "https://github.com/"
```
#### GOLANG download 
From https://golang.org/dl/ .
```bash
wget https://dl.google.com/go/go1.13.4.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.13.4.linux-amd64.tar.gz
```
(does not work as root, without sudo)

Create folders for installation:
```bash
mkdir -p $HOME/go/bin $HOME/go/pkg $HOME/go/src 
```
Add environment variables for LXTerminal:
```bash
vi $HOME/.bashrc
```
or other terminals:
```bash
vi $HOME/.profile
...
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin
```
Verify:
```bash
go version
```
(GOROOT - folder where the tar was unzipped ):

For gotest to work enable execution on /tmp:
```bash
sudo vi /etc/fstab
```
remove noexec from tmp. save and remount tmp:
```bash
sudo mount -o remount /tmp
```
Verify:
```bash
mount |grep /tmp
```
#### Upgrade GO version
Remove previous version first:
```bash
sudo rm -r /usr/local/go/
```
Download and unzip new version:
```bash
sudo tar -C /usr/local -xzf <new version>
```
#### LiteIDE download
From https://github.com/visualfc/liteide/releases .
```bash
wget https://github.com/visualfc/liteide/releases/download/x36.1/liteidex36.1.linux64-qt5.5.1.AppImage
```
* version with qt 5.x.y
* version as AppImage
* view->options->LiteEditor->Fonts&Colors->Sublime

Create desktop shortcut:
```bash
vi ~/Desktop/liteide.desktop
chmod +x ~/Desktop/liteide.desktop
```
With contents:
```bash
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Icon=/home/tudi/Pictures/Oxygen-Icons.org-Oxygen-Categories-applications-system.ico
Exec=/home/tudi/liteidex36.1.linux64-qt5.5.1.AppImage
Name=LiteIDE
GenericName=IDE
```
#### Godoc
Be aware below installs older version of go tools.
```bash
sudo apt-get install golang-go.tools
godoc -http=:6060
# Navigate to http://localhost:6060
```
