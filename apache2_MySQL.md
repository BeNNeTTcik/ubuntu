# ubuntu Apache2 MySQL:
 1. [README](README.md)
 7. [MySQL](#mysql)
 7.1. [New User and DB](#user)

### 7. MySQL install and connect: <a name="mysql"></a>
```sudo su``` - root permissions\
```apt install mysql-server``` - install mysql-server\
```systemctl enable mysql.service``` - add MySQL Server to auto-start after reboot\
```systemctl start mysql.service``` - start MYSQL Server\
```status mysql.service``` - check status of the server\
```mysql``` - connect to MySQL Server\
```mysql> ALTER USER root@localhost IDENTIFIED WITH mysql_native_password BY '<f.g. admin>';``` - change the password of the root’s account\
```mysql>exit``` - leave from MySQL Server\
```mysql -u root -p``` - how connect on MySQL\
```mysql_secure_installation``` - secure options on MySQL server for root and dif users.

### 7.1. New user create and preapare a database: <a name="user"></a>
```mysql -u root -p``` - login lika a root\
```CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'your_password';``` - create new user with password\
```CREATE DATABASE new_db;``` - new DB (database)\
```GRANT ALL PRIVILEGES ON new_db.* TO 'new_user'@'localhost';``` - give all permissions to administrate DB\
```FLUSH PRIVILEGES;``` - update permissions on server\
```exit``` - exit from mysql.
