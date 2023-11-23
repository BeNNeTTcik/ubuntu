 1. [README](README.md)\
 4. [MySQL](#mysql)

### 4. MySQL install and connect: <a name="mysql"></a>
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
