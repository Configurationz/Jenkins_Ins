### Setting Up an Nginx Reverse Proxy
-------------------------------------

> Step 1 - Install Nginx from Default Repositories
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

> Step 2 (optional) - Install Nginx from Official Repository

- Add a Security Key - In a terminal window, enter the following:
```
sudo wget https://nginx.org/keys/nginx_signing.key
```
```
sudo apt-key add nginx_signing.key
```
This downloads the signing key for Nginx, which verifies that you’re downloading authentic software.

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

* Install Latest Release of Nginx. To install the latest release of Nginx, use the commands:
```
sudo apt-get remove nginx-common
```
```
sudo apt-get update
```
```
sudo apt-get install nginx
```
  
> Step 3: Start Nginx and Configure to Launch on Reboot. To start Nginx:
```
sudo systemctl start nginx
```
- To enable Nginx:
```
sudo systemctl enable nginx
```
- To check Nginx is running:
```
sudo systemctl status nginx
```
*The output should show you the service is active (running).*

> Step 4: Unlink Default Configuration File

- In the terminal, enter the following:
```
sudo unlink /etc/nginx/sites-enabled/default
```
> Step 5: Create New Configuration File

- To create a new configuration file, enter:
```
cd /etc/nginx/sites-available/
```
```
sudo vi custom_server.conf
```
- Replace custom_server with a name that’s meaningful to you. In the new file, enter:
```
server {
    listen 80;
    location / {
        proxy_pass http://192.x.x.2;
    }
}
```
  
- This is a very basic Nginx reverse proxy example. Nginx is set to listen for all traffic on port 80 for all traffic.

- The proxy_pass command directs all traffic on port 80 to http://my_server. Just change http://my_server to the location of your choice, 
  and Nginx will intercept client requests and route them to the location you specify. Once you’ve finished, save the file and exit.

> Step 6: Link and Activate Configuration File

- To activate the new Nginx file, enter:
```
ln -s /etc/nginx/sites-available/custom_server.conf /etc/nginx/sites-enabled/custom_server.conf
```
- As usual, replace custom_server with the name of the configuration file you created in Step 5.

> Step 7: Test and Restart Nginx

- To test Nginx:
```
sudo service nginx configtest
```
- To restart Nginx:
```
sudo service nginx restart
```

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
