1. install
sudo apt install -y mariadb-server

2. get status
systemctl status mariadb

*sudo systemctl restart mariadb.service
*sudo systemctl enable mariadb.service

version: mariadb --version

3. security configuration (optional)
sudo mysql_secure_installation

By default, MariaDB on Ubuntu uses unix_socket to authenticate user login.
Basically you can use username and password of the OS to log into MariaDB console:

sudo mariadb -u root
*exit;

4. create database
a. connect with root
b. create database <db_name> default character set utf8 default collate utf8_bin;
c. SHOW DATABASES LIKE 'db_name%';

5. create user
a. grant access locally
GRANT ALL PRIVILEGES ON db_name.* to user_name@'localhost' IDENTIFIED BY 'user_password';

b. grant access from any other host
GRANT ALL PRIVILEGES ON db_name.* to user_name@'%' IDENTIFIED BY 'user_password';

c. verify: show grants for user_name;

6. get more info:
SHOW STATUS;
SHOW VARIABLES;

7. allow remote connections:
a. update server configuration
sudo vi /etc/mysql/mariadb.conf.d/50-server.cnf
change: bind-address = 127.0.0.1 to bind-address = 0.0.0.0

sudo systemctl restart mariadb.service

b. check socket has opened:
sudo apt-get install net-tools
sudo netstat -anp | grep 3306
