### Environment variables
Add environment variables for LXTerminal:
```bash
vi $HOME/.bashrc
```
or other terminals (ex. MX Linux):
```bash
vi $HOME/.profile
...
export GOROOT=$HOME/go
export PATH=$PATH:$GOROOT/bin
```
### GOLANG download 
From https://golang.org/dl/ .
```bash
wget https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz
tar -C $HOME -xzf go1.13.5.linux-amd64.tar.gz
```
Verify:
```bash
go version
```
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
### Upgrade GO version
Remove previous version first:
```bash
sudo rm -r $GOROOT
```
Download and unzip new version:
```bash
tar -C $HOME -xzf <new version>
```
### Godoc
Be aware below installs older version of go tools.
```bash
sudo apt-get install golang-go.tools
godoc -http=:6060
# Navigate to http://localhost:6060
```
### Resources
```html
https://dev.to/maelvls/why-is-go111module-everywhere-and-everything-about-go-modules-24k
https://dave.cheney.net/2018/07/14/taking-go-modules-for-a-spin
https://dave.cheney.net/2018/07/16/using-go-modules-with-travis-ci
```
