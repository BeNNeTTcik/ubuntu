### 6.a. Webmin install and connect: <a name="webmin"></a>
### 6.b. Usermin install and connect: <a name="usermin"></a>

## Webmin:

```sudo su```\
```cd /var```\
```vi /etc/apt/sources.list``` - edit file source.list\
```
...
deb http://download.webmin.com/download/repository sarge contrib
...

```
```wget http://www.webmin.com/jcameron-key.asc```\
**If u will have problem with the key:\
```cat jcameron-key.asc | gpg --dearmor >/etc/apt/trusted.gpg.d/jcameron-key.gpg```\**
```apt-get update```\
```apt-get install webmin```\
```ufw allow 10000/tcp``` - allow to communicate on port 10000\
Check on web browser:
https://ip_your_domain:10000



## Usermin:

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
