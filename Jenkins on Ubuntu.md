### Installation & Configuration
--------------------------------

> Initial Steps
> -------------

- Update the package definitions
```
sudo apt update
```

- Search for a specific openjdk (_8,11,17,19_)
```
sudo apt-cache search openjdk
```

- Check which jdk version we may download
```
sudo apt-cache madison openjdk-11-jdk
```

- Install Java 11
```
sudo apt install openjdk-11-jdk -y
```

- Install Maven
```
sudo apt install maven -y
```

- Verify Installations (if required)
```
java -version
```
```
mvn --version
```

* We may need to install multiple versions of Java/Maven/etc. so we need to be very careful with environment variables.
  So, we can use the following command to set a specific java as a temporary default.
```
export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH"
```

> Jenkins Installations
>-----------------------

* Step1 - Execute the commands sequentiallly

  [Jenkins Debian Packages](https://pkg.jenkins.io/debian-stable/)
  

* Step2 - Verify Jenkins Service
```
sudo systemctl status jenkins.service
```

* Step 3 - Navigate to `http://<publicip>:8080`

* Step4 - Continue with Jenkins Installation
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
* Copy the password & paste on Jenkins page
  -  Customize Jenkins: Install suggested plugins
  -  Getting Started:
  -  Create First Admin User:
  -  Instance Configuration: `http://<privateip>:8080/` & then Save and Finish.
  -  Jenkis is Ready: Start using Jenkins
 
* Next login CLI to check for users:
```
sudo cat /etc/passwd
```
* A new user called as *jenkins* is created and the group name is *Jenkins* with the home directory of `/var/lib/jenkins`

* From the Jenkins UI, no matter what user you are logged in as, the low level commands are executed as the *jenkins* user
* Now lets try to do `sudo apt update` from the Jenkins UI.

* From Jenkins UI we can do anything that the linux user jenkins can do.
* From Jenkins UI if we need to do installations etc, we need sudo permissions without password.
* So Lets configure linux jenkins user to have sudo permissions without password prompts
```
sudo visudo
```
* Next configure the *jenkins* user without password prompts
```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
jenkins ALL=(ALL:ALL) NOPASSWD:ALL
```

For further Details [Ref here](https://directdevops.blog/2022/05/02/devops-classroomnotes-02-may-2022/)

:octocat:







