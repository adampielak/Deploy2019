https://www.cockroachlabs.com/docs/stable/install-cockroachdb.html

1. start as localhost to create database (only root can create database):

cockroach start --insecure --host=localhost

2. create database:

a. connect with sql client on same node: cockroach sql --insecure
b. CREATE DATABASE <db>;

3. create user to connect remotely:

a. create user <user>;
b. grant create, select, insert on database <db> to <user>;
c. show grants on <db>;

4. start database for remote connection:
cockroach start --insecure --host=1.1.1.1
