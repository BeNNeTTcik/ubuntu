# ubuntu Apache2 project
 1. [Startup files.](#start)
 2. [Install apache2](#install)
 3. [Additional Modules](#modules)


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

**Basic information about Apache2 and directories, which is used.**

Whole website are storage in ```/var/www/html```. Directory to Virtual Host is ```/etc/apache2/sites-enabled```. Virtual Host allows you to split different websites that are located under the same IP address. Inside you will find a file called **000-default.conf**, which can be modified with "vi" or "nano" (```sudo apt install nano``` before use).

Create domain "www.mojastrona.pl" and connect domain with "index.html" use this commend: ```vi /etc/apache2/sites-enabled/000-default.conf```. You will see a file similar to the one below:
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/c6c34685-f3d1-4704-94d1-a989077ecb2f)\ 
Now we need to change "ServerAdmin" on www.mojastrona.pl. If u change the path of the "index.html" u should change this line on right path. Thats all u can leave form text editor. Remember to save changes.

### 3. Additional modules: <a name="modules"></a>

| Module   | Installion script       | Short informations |
|---------|----------------------|-------------------|
| [userdir](#userdir) | sudo a2enmod userdir |      allowing multiple users to host content within the same origin, like http//domain.xyz/~user             |
| [rewrite](#rewrite) | sudo a2enmod rewrite |     can be used to redirect one URL to another URL; allows manipulation of the entire URL address     | 
| [ssl](#ssl)     | sudo a2enmod ssl     |           works on OpenSSL engine and provide the cryptography        |

## Userdir configuration: <a name="userdir"></a>

Before configuration we should have user on the VM. To add user use this commend ```sudo adduser <name of the user>```.\
Configuration userdir:\
```su $<name of created user>``` - we change root client on user client.\
```mkdir ./public_html && chmod 755 ./public_html``` - in home catalog we create a new folder and change folder permissions on 755.\
```exit``` - leave from user client to root client.\
```service apache2 restart``` - restart apache2 services all the time after changes.\
```cd /home/<name of the user>/public_html``` - change directory on public_html, because we need create a new file "index.html".\
```vi index.html``` - u can replace "vi" on "nano" and create a file.\
Inside file "index.html" write simple website to check configuration:
```<html>```\
``` <body>```\
 ``` <title> Mateusz Swiat </title>```\
``` </body>```\
```</html>```\

After all u should open website after ip or domain on your web browser:\
In URL use IP to connect:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/0fcc56a5-c390-4844-a2b8-b119465f2cf9)\
In URL use domain name to connect:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/d9fa587a-db84-4efd-bc19-963453cc256f)\



## Rewrite configuration: <a name="rewrite"></a>

Good tutorial *[How To Rewrite URLs with mod_rewrite for Apache](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04)*

## SSL configuration: <a name="ssl"></a>

![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/410300b3-4d7f-434c-8386-25f4b03ed6e2)
