> Opensource Ecommerce B2C and B2B Marketplace using Nodejs and Angular (www.spurtcommerce.com)
>----------------------------------------------------------------------------------------------
Minimal Hardware Configuration
* CPU — 1 Core CPU
* RAM — 1 GB RAM
* Storage — 16 GB Storage
* Operating System — Ubuntu 20.04.4 LTS

> Prerequisites
> -------------
If we want to deploy Spurtcommerce into our server, following softwares needs to be installed in our system.
* Node Js Installation (Version — 14.x)
* Apache Installation
* MySQL Installation
* Imagemagick Installation
* Angular Installation

> Node Js Installation (Version — 14.x)
>--------------------------------------
- The Back-end API of Spurtcommerce is on NodeJS (v.14.x). Thus, it requires the installation of the same version of NodeJS.
- Use the following commands to install the required version of NodeJS in your system.
```
sudo apt-get update
```
```
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```
```
sudo apt-get install -y nodejs
```
```
sudo apt-get install -y build-essential
```
```
sudo npm install forever -g
```
```
sudo npm install apidoc -g
```
- NodeJS installation is successful.

> Apache Installation
> -------------------
```
sudo apt update
```
```
sudo apt install apache2 -y
```
```
sudo a2enmod proxy
```
```
sudo a2enmod proxy_http
```
```
sudo a2enmod headers
```
```
sudo systemctl restart apache2
```
- Completed successful installation of Apache.

> Mysql Installation
> ------------------
```
sudo apt-get install mysql-server -y
```
```
sudo mysql -u root
```
```
mysql > SELECT User, Host, plugin FROM mysql.user;
```
```
mysql > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
```
mysql> FLUSH PRIVILEGES;
```
```
mysql> exit
```

>Imagemagick Installation
>------------------------
```
sudo apt update
```
```
sudo apt install imagemagick -y
```

>Angular Installation
>--------------------
```
npm install -g @angular/cli
```
*NOTE: Required minimum 4gb RAM for installing Angular CLI*


























