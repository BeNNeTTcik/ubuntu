# ubuntu Apache2 project
 1. [Startup files.](#start)
 2. [Install apache2](#install)
 3. [Create domains](#create)
 4. [Apache2 Modules](apache2_mods.md)
 5. [Apache2 PHP](apache2_php.md)
 6. [Apache2 MySQL](apache2_MySQL.md)


### 1. Startup files: <a name="start"></a>

#### Link to download Ubuntu server: 
*[Ubuntu Server 20.04.3 LTS](https://ubuntu.com/download/server)* 

#### Link to download Oracle VM: 
*[Oracle VM](https://www.virtualbox.org/wiki/Downloads)*

#### How to install Ubuntu Server on Oracle VM:
*[How to Install Ubuntu 20.04 LTS on VirtualBox in Windows 10](https://www.youtube.com/watch?v=x5MhydijWmc)*

#### Configuration Ubuntu Server:

- Language: .....
- Install update avaliable: "Continue without updating"
- Keyboard confiuguration: "Done"
- Choose type of install: "Done"
- Network connections: "Done"
- Configure proxy: "Done"
- Configure Ubuntu archive mirror: "Done"
- Guided storage configuration: "Done"
- Storage configuration: "Done" -> "Continue"
- Profile setup: ...
- SSH Setup: X "Install OpenSSH server"
- Import SSH identity "No"
- Featured Server Snaps: "Done"

After installtion use login and password and enter the system. READY!!!
![image](https://github.com/BeNNeTTcik/ubuntu/assets/42866234/ca14b95c-8087-41d0-82fa-c63f393fd292)

### 2. Install apache2. <a name="install"></a>
Before installetion apache2 on server, we should update software on VM (Virtual Machine). Use code below to update the software.
```sudo apt update```
Next step is install apache2 on server. Use code below:
```sudo apt install apache2```
You will see information about the memory that will be used for the installation and of course type: "y" to continue the installation.

CORE THING!!!\
If u use VM VirtualBox go to:
Settings -> Network -> Connected to: Host Only -> Name:VirtualBox Host-Only Ethernet Adapter -> Listening mode: Allow Everyone.
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/4d05faa0-8aee-4dd7-9cc6-d3fbcb649f49)

Define two domain: 
 - Linux - ```vi /etc/hosts``` add <IP> example.com www.example.com and <IP> test.com www.test.com. IP u can check by command: ```hostname -I```\
 - Windows C:\Windows\System32\drivers\etc\hosts add <IP> example.com www.example.com and <IP> test.com www.test.com.\

**Basic information about Apache2 and directories, which is used.**

Whole website are storage in ```/var/www/html```. Directory to Virtual Host is ```/etc/apache2/sites-enabled```. Virtual Host allows you to split different websites that are located under the same IP address. Inside you will find a file called **000-default.conf**, which can be modified with "vi" or "nano" (```sudo apt install nano``` before use).

Create domain "www.mojastrona.pl" and connect domain with "index.html" use this commend: ```vi /etc/apache2/sites-enabled/000-default.conf```. You will see a file similar to the one below:
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/c6c34685-f3d1-4704-94d1-a989077ecb2f)\ 
Now we need to change "ServerAdmin" on www.mojastrona.pl. If u change the path of the "index.html" u should change this line on right path. Thats all u can leave form text editor. Remember to save changes.

### 3. Create domains <a name="create"></a>

Tutorial:\
[How configure 2 domains](https://www.youtube.com/watch?v=IH9MmUQiOI4)

```sudo su``` - root permissions\
```mkdir -p /var/www/mojastrona.pl/public_html``` - create first domain directory\
```mkdir -p /var/www/szyfrowana.pl/public_html``` - create secound ssl domain directory\
```chmod -R 755 /var/www``` - "R" all files and directory got permission 755\
```cd /var/www``` - move to /var/www\
```vi ./mojastrona.pl/public_html/index.html``` - create website for domain example.com\
```<h1>mojastrona.pl ez</h1>``` - website\
```vi ./szyfrowana.pl/public_html/index.html```  - create website for domain test.com\
```<h1>szyfrowana.pl ez</h1>``` - website\
```cd /etc/apache2/sites-avaliable/``` - move to /etc/apache2/sites-avaliable\
```cp ./000-default.conf mojastrona.pl.conf``` - copy 000-default.conf to mojastrona.pl.conf\
```cp ./default-ssl.conf szyfrowana.pl.conf```- copy default-ssl.conf to szyfrowana.pl.conf\
```vi mojastrona.pl.conf``` - edit VirtualHost for mojastrona.pl\
```
...
ServerName mojastrona.pl
ServerAlias www.mojastrona.pl
DocummentRoot /var/www/mojastrona.pl/public_html/
...
```
```vi test.com.conf``` - edit VirtualHost for szyfrowana.pl\
```
...
ServerName szyfrowana.pl
ServerAlias www.szyfrowana.pl
DocummentRoot /var/www/szyfrowana.pl/public_html/
...
```
```a2ensite mojastrona.pl.conf``` - activation VirtualHost for domain mojastrona.pl\
```a2ensite szyfrowana.pl.conf``` - activation VirtualHost for domain szyfrowana.pl\
```a2dissite 000-default.conf``` - deactivation VirtualHost default\
```service apache2 restart``` - restart apache2 services\

