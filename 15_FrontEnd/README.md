### 1. Install Debian base
```bash
apt install sudo vim gdebi
apt-get install task-xfce-desktop
```

### 2. Chrome
```bash
sudo vi /etc/apt/sources.list
# add:
deb http://dl.google.com/linux/chrome/deb/ stable main
```
```bash
wget https://dl-ssl.google.com/linux/linux_signing_key.pub
sudo apt-key add linux_signing_key.pub
sudo apt-get update
sudo apt-get install google-chrome-stable
```
### 3. Visual Studio Code
```html
https://code.visualstudio.com/Download
```
### 4. Node.JS
a. install nvm (https://github.com/creationix/nvm), check latest version:
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```
verify:
```bash
nvm --version
# exit terminal if it does not work
```
b. install latest nodejs version:
```bash
nvm install node
```
verify version: 
```bash
node -v
npm -v
```
c. With snap:
```bash
sudo snap install --edge --classic node
```
If npm not found, add it to the path:
```bash
sudo snap search npm
```
### 5. SASS Compiler
```js
npm install -g sass
```

```bash
sass scss/style.scss css/style.css
```
Delete style.css and map files after debugging as because different map the IDE will have issues with SASS compilation.
