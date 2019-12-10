### Environment variables
Add environment variables for default bash shell in:
```bash
vi $HOME/.bashrc
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin
# if not working try $HOME/.profile
```
### GOLANG download 
From https://golang.org/dl/ .
```bash
wget https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.13.5.linux-amd64.tar.gz
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
https://github.com/golang/go/wiki/Modules
https://www.youtube.com/watch?v=F8nrpe0XWRg&list=PLq2Nv-Sh8EbbIjQgDzapOFeVfv5bGOoPE&index=3&t=0s
https://dev.to/maelvls/why-is-go111module-everywhere-and-everything-about-go-modules-24k
https://dave.cheney.net/2018/07/14/taking-go-modules-for-a-spin
https://dave.cheney.net/2018/07/16/using-go-modules-with-travis-ci
```
