### GOLANG download 
From https://golang.org/dl/ .
```bash
wget https://dl.google.com/go/go1.13.5.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.13.5.linux-amd64.tar.gz
```
(does not work as root, without sudo)

### Environment variables
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

Create folders for installation:
```bash
mkdir -p $GOPATH/bin $GOPATH/pkg $GOPATH/src 
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
sudo rm -r /usr/local/go/
```
Download and unzip new version:
```bash
sudo tar -C /usr/local -xzf <new version>
```

### Godoc
Be aware below installs older version of go tools.
```bash
sudo apt-get install golang-go.tools
godoc -http=:6060
# Navigate to http://localhost:6060
```
