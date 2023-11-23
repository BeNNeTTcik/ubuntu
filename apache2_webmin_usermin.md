 6.a. [Webmin](#webmin)
 6.b. [Usermin](#usermin)

### 6.a. Webmin install and connect [1][2]: <a name="webmin"></a>

```sudo su``` - root permissions\
```cd /var``` - move to /var direcotry\
```vi /etc/apt/sources.list``` - edit file source.list, where we adding a repository\
```
...
deb http://download.webmin.com/download/repository sarge contrib
...

```
```wget http://www.webmin.com/jcameron-key.asc``` - download the key form the web server\
```sudo apt-key add jcameron-key.asc``` - try add the key in trusted.pgp
**If u will have problem with the key in file trusted.pgp:\
```cat jcameron-key.asc | gpg --dearmor >/etc/apt/trusted.gpg.d/jcameron-key.gpg```\**
```apt-get update``` - update the files\
```apt-get install webmin``` - install webmin\
```ufw allow 10000/tcp``` - allow to communicate on port 10000\
Check on web browser:
https://ip_your_domain:10000

### 6.b. Usermin install and connect: <a name="usermin"></a>

![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/62d6aee8-70f5-4a5f-84d9-d3e8c577a52c)
```sudo su```\
```cd /var```\
```wget https://sourceforge.net/projects/webadmin/files/usermin/2.005/usermin_2.005_all.deb```\
```dpkg --install usermin_2.005_all.deb```\
```systemctl start usermin```\
```systemctl enable usermin```\
```ufw allow 20000``` - allow to communicate on port 10000\

Check on web browser:
https://ip_your_domain:20000


SOURCE:
[1. Install webmin - Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-16-04)
[2. Deprecated trusted.pgp](https://github.com/webmin/webmin/issues/1629)
