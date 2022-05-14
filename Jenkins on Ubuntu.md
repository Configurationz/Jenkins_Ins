### Installation & Configuration
--------------------------------

> Initial Steps
> -------------

- Update the package definitions
```
sudo apt update
```

- Search for a specific java version 
```
sudo apt-cache search openjdk
```

- Install Java 11
```
sudo apt install openjdk-11-jdk -y
```

> Jenkins Installation
>----------------------

* Step1 - Execute the commands sequentiallly

  [Jenkins Debian Packages](https://pkg.jenkins.io/debian-stable/)
  
* Step2 - Verify Jenkins Service
```
sudo systemctl status jenkins.service
```

* Step 3 - Navigate to http://<publicip&gt;:8080

* Step4 - Continue the installation
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
* Copy the password & paste on Jenkins page


















