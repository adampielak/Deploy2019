1. install git:
sudo apt-get update
sudo apt install git

2. download gogs from 
https://gogs.io/docs/installation/install_from_binary

3. untar:
tar -xvf <archive>

4. cd gogs

5. ./gogs web

6. connect:
http://192.168.1.26:3000/install

7. add ip for gogs server in pg_hba.conf in /etc/postgresl/9.6/main

8. create database where gogs would be installed.

9. sync servers to one NTP

10. set origin remote in case repository was initialized from gogs web:
git remote set-url origin https://github.com/LongKnight/git-basics.git

git commit -m "something"
git push
