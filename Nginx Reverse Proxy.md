###Setting Up an Nginx Reverse Proxy
------------------------------------

> Step 1: Install Nginx from Default Repositories
- Open a terminal window and enter the following:
```
sudo apt-get update
```
- Allow the package manager to finish refreshing the software lists, then enter the following:
```
sudo apt-get install nginx
```
- Allow the process to complete.

*Note: This is the easiest way to install Nginx on CentOS or Ubuntu, but it may not load the latest stable release. 
Move on to Step 2 to add and install from the Nginx software repositories.*

> Step 2 (optional): Install Nginx from Official Repository

- Add a Security Key - In a terminal window, enter the following:
```
sudo wget https://nginx.org/keys/nginx_signing.key
```
```
sudo apt-key add nginx_signing.key
```
- This downloads the signing key for Nginx, which verifies that you’re downloading authentic software.

- Open sources.list File for Editing In the terminal, enter the following:
```
sudo vi /etc/apt/sources.list
```
- At the end of the file, Add Nginx Sources to Repository List. Enter the following lines in the /etc/apt/sources.list file you just opened:
```
deb https://nginx.org/packages/mainline/debian/ <CODENAME> nginx
```
```
deb-src https://nginx.org/packages/mainline/debian/ <CODENAME> nginx
```
- Replace <CODENAME> with your distribution of Linux. Save and exit the file.


