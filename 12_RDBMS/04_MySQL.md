### 1. Download community edition (Debian bundle)
```html
https://dev.mysql.com/downloads/mysql/
```
- Choose ubuntu
- Choose 18.04 64b
```html
https://dev.mysql.com/get/Downloads/MySQL-8.0/mysql-server_8.0.11-1ubuntu18.04_amd64.deb-bundle.tar
```
### 2. Extract
```bash
tar -xvf mysql-server_*.deb-bundle.tar
```
### 3. Install prerequisites
```bash
sudo apt-get install libaio1 libsasl2-2 libnuma1 libmecab2 perl psmisc
```
### 4. Preconfigure
```bash
sudo dpkg-preconfigure mysql-community-server_*.deb
# leave root empty for unix socket authentication
# use legacy connections for now
```
### 5. Install
```bash
sudo dpkg -i mysql-common_8.0.11-1ubuntu18.04_amd64.deb
sudo dpkg -i mysql-community-client-core_8.0.11-1ubuntu18.04_amd64.deb
sudo dpkg -i mysql-community-client_8.0.11-1ubuntu18.04_amd64.deb
sudo dpkg -i mysql-client_8.0.11-1ubuntu18.04_amd64.deb 
sudo dpkg -i mysql-community-server-core_8.0.11-1ubuntu18.04_amd64.deb 
sudo dpkg -i mysql-community-server_8.0.11-1ubuntu18.04_amd64.deb 
```
### 6. Check Installation
- data directory: /var/lib/mysql
- connect:
```bash
sudo mysql -u root
```
### 7. Create database
```sql
create database devops default character set utf8 default collate utf8_bin;
```
### 8. Create database user
```sql
CREATE USER 'develop'@'192.168.1.%' IDENTIFIED BY 'develop';
GRANT ALL PRIVILEGES ON devops.* to develop@'192.168.1.%';
/* reload privileges now: FLUSH PRIVILEGES; */
```
On linux mint 18.3:
```bash
sudo apt install mysql-server
mysql -u root -p
```
```sql
grant all privileges on *.* to 'root'@'%' identified by 'root';
flush privileges;
```
