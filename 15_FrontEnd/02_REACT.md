1. install nvm (https://github.com/creationix/nvm), check latest version:
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash

verify:
nvm --version
(exit terminal if it does not work)

2. install latest nodejs version:
nvm install node

verify version: 
node -v
npm -v

3. create React app:
a. install prerequisites:
npm install -g create-react-app

b. create the app scaffold:
create-react-app myapp

4. test app
cd myapp
npm start

5. create production files:
npm run build

6. update app on RAM disk:
cd myapp
git init
git remote add origin git@github.com:TudorHulban/react01.git

check:
git remote -v

git fetch origin
git reset --hard origin/master
