### Installing MySQL on Ubuntu 20.04
------------------------------------

   - For installing, update the package index on your server if you’ve not done so recently -
   
         sudo apt update
 
   - To install MySQL, run the following command - 
        
         sudo apt install mysql-server -y

   - The MySQL server should start automatically orelse check with following command -

         sudo systemctl status mysql.service

   - If the server is not running correctly, enter the following command to restart it -
        
         sudo service mysql restart


> **Configuration** -

   - Run the security script with sudo -

         sudo mysql_secure_installation
        
   - We can edit the files in /etc/mysql/ to configure the basic settings – log file, port number, etc. For example, to configure MySQL to listen for connections            from network hosts, in the file /etc/mysql/mysql.conf.d/mysqld.cnf, change the bind-address directive to the server’s IP address:

         bind-address = 192.168.0.5

     *Note: Replace 192.168.0.5 with the appropriate address, which can be determined via ip address show.*
     
     _Also check /etc/mysql/my.cnf or /etc/mysql/mysql.conf.d/mysqld.cnf location for changing_

         bind-address = 0.0.0.0

   - After making a configuration change, the MySQL daemon will need to be restarted:
   
         sudo systemctl daemon-reload

         sudo systemctl restart mysql.service
--- 

Creating a New User & Granting Permissions in MySQL
---------------------------------------------------

1. **Start MySQL Shell** -
      
      ```
      sudo mysql
      ```
    
    - There are more than one way to work with a MySQL server, but this article focuses on the most basic and compatible approach, the mysql shell.
    - At the command prompt, run the following command to launch the mysql shell and enter it as the root user:
      
      ```
      /usr/bin/mysql -u root -p
      ```

2. **Creating a New User** -

    *Note: If your root MySQL user is configured to authenticate with a password, you will need to use a different command to access the MySQL shell. The following will  run your MySQL client with regular user privileges, and you will only gain administrator privileges within the database by authenticating with the correct password:*

         mysql -u root -p
 
    - Once we have access to the MySQL shell prompt, we can create a new user with a CREATE USER statement. These follow this general syntax:
        
        ```
        CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'mypass';
        ```
        
        ```
        CREATE USER 'myuser'@'%' IDENTIFIED BY 'mypass';
        ```
 
 3. **Granting User Permissions** -
 
    - The general syntax for granting user privileges is as follows:
        
        ```
        GRANT ALL ON *.* TO 'myuser'@'localhost';
        ```
        
        ```
        GRANT ALL ON *.* TO 'myuser'@'%';
        ```
    
    - Following this, it’s a good practice to run the FLUSH PRIVILEGES command. This will free up any memory that the server cached as a result of the preceding CREATE       USER and GRANT statements:
        
        ```
        FLUSH PRIVILEGES;
        ```
    
    - Now exit MySQL shell
      
      ```
      exit
      ```    
---      
```ini
 
- Run this GRANT statement, replacing 'myuser' with your own MySQL user’s name, to grant these privileges to your user:
        
   GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
        
*NOTE: This statement also includes WITH GRANT OPTION. This will allow your MySQL user to grant any permissions that 
       it has to other users on the system.
       Warning: Some users may want to grant their MySQL user the ALL PRIVILEGES privilege, which will provide them with 
       broad superuser privileges asking to the root user’s privileges, like so:*
        
   GRANT ALL PRIVILEGES ON *.* TO 'myuser'@'localhost' WITH GRANT OPTION;
        
- If we need to revoke a permission, the structure is almost identical to granting it -
      
   REVOKE type_of_permission ON database_name.table_name FROM 'username'@'host';
      
*NOTE: When revoking permissions, the syntax requires that you use FROM,instead of TO which you used when granting the permissions.
  
- You can review a user’s current permissions by running the SHOW GRANTS command -
      
   SHOW GRANTS FOR 'username'@'host';
      
- Just as you can delete databases with DROP, you can use DROP to delete a user -
        
   DROP USER 'username'@'localhost';
        
- After creating your MySQL user and granting them privileges, you can exit the MySQL client -
        
   exit
        
- In the future, to log in as your new MySQL user, you’d use a command like the following - 
        
   mysql -u myuser -p
        
- The -p flag will cause the MySQL client to prompt you for your MySQL user’s password in order to authenticate.

```
---
        

4. Now try to login from the same local m/c using following command -  
      ```
      sudo mysql -u myuser -p
      ```
   - Enter the password which we created while creating 'myuser' (new user) in MySQL. We should be able to login into MySQL shell.
   - Now check for the current user in MySQL shell. 
    ``` 
    select USER();
    ```
    ```
    mysql> select USER();
    +------------------+
    | USER()           |
    +------------------+
    | myuser@localhost |
    +------------------+
    1 row in set (0.00 sec)
    ```

   - Now we are successfully able to login into MySQL shell with username as 'myuser'.
   - So, exit from this local m/c & will try to login from a remote m/c. 
   - Since we only need to verify whether remote login is possible, just install MySQL-Shell on the remote m/c.
5. Execute the following commands one by one -
   ```
   sudo apt-get update
   ```
   ``` 
   sudo snap install mysql-shell
   ```
   
   - Since, mysql-shell is not working, so -
   ```
   sudo apt install mysql-client-core-8.0
   ```
   
   - Now let's try logging-in from remote m/c
   ```
   mysql -h 18.218.146.245 -u myuser -p
   ```
   - Enter the password of the user which we created in our local m/c.
   - And hence, we're able to login from a remote m/c.
   - So, try the following command now -
   ```
   select USER();
   ```
   ```
   mysql> select USER();
   +----------------------+
   | USER()               |
   +----------------------+
   | myuser@3.145.145.246 |
   +----------------------+
   1 row in set (0.00 sec)
   ```
   
---
UNINSTALL OR COMPLETELY REMOVE MYSQL FROM UBUNTU 20.04
------------------------------------------------------

While upgrading from Ubuntu 18.04 to Ubuntu 20.04, we faced some issues which were unexpected.
This incident was caused by MySQL server update, while setting up the mysql by apt, it gets hang on the server and will not work, leaving it around for one hour.
So I decided to remove the MySQL server and reinstall again. Execute the following commands one by one -
   ```
   sudo apt-get remove --purge mysql*
   ```
   ```
   sudo apt-get purge mysql*
   ```
   ```
   sudo apt-get autoremove
   ```
   ```
   sudo apt-get autoclean
   ```
   ```
   sudo apt-get remove dbconfig-mysql
   ```
   ```
   sudo apt-get dist-upgrade
   ```

[Ref.0 - Installation](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)

[Ref.1 - Ubuntu documentation](https://ubuntu.com/server/docs/databases-mysql)

[Ref.2 - Creating User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

[Ref.3 - Installing MySQL Shell on Linux](https://dev.mysql.com/doc/mysql-shell/8.0/en/mysql-shell-install-linux-quick.html)

[Ref.4 - Installing MySQL Shell on Windows](https://dev.mysql.com/doc/mysql-shell/8.0/en/mysql-shell-install-windows-quick.html)

[Ref.5 - Remote login](https://stackoverflow.com/questions/16287559/mysql-adding-user-for-remote-access)

[Ref.6 - Uninstalling MySQL](https://linuxscriptshub.com/uninstall-completely-remove-mysql-ubuntu-16-04/)

