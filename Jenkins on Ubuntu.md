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

* From Jenkins UI we can do anything that the linux user jenkins can do.
* From Jenkins UI if we need to do installations etc, we need sudo permissions without password.
* So Lets configure linux jenkins user to have sudo permissions without password prompts
```
sudo visudo
```
* Now add the jenkins user to sudoers group with no password
`jenkins ALL=(ALL:ALL) NOPASSWD:ALL `


For any queries [Ref here](https://directdevops.blog/2022/05/02/devops-classroomnotes-02-may-2022/)

:octocat:







