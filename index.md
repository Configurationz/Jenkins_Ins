## Jenkins Installation & Configuration in ubuntu 
--------------------------------------------------

### Pre-requisites:

- Update the package definitions
```
sudo apt update
```

- We need to install java before we install jenkins because without java, jenkins wouldn't work 

- So, search for an openjdk (_8,11,17,19_) to install
```
sudo apt-cache search openjdk
```

- Check for a specific openjdk version we need to install
```
sudo apt-cache madison openjdk-11-jdk
```

| openjdk-11-jdk | 11.0.18+10-0ubuntu1-20.04.1 | http://azure.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages |
| openjdk-11-jdk | 11.0.18+10-0ubuntu1~20.04.1 | http://azure.archive.ubuntu.com/ubuntu focal-security/main amd64 Packages |
| openjdk-11-jdk | 11.0.7+10-3ubuntu1 | http://azure.archive.ubuntu.com/ubuntu focal/main amd64 Packages |

- Let's install Java11
```
sudo apt install openjdk-11-jdk -y
```

- Also, Install Maven
```
sudo apt install maven -y
```

- Verify Installations (if required)
```
java -version
```
> openjdk version "11.0.18" 2023-01-17                                                                                                                    
> OpenJDK Runtime Environment (build 11.0.18+10-post-Ubuntu-0ubuntu120.04.1)                                                                        
> OpenJDK 64-Bit Server VM (build 11.0.18+10-post-Ubuntu-0ubuntu120.04.1, mixed mode, sharing)


```
mvn --version
```
> Apache Maven 3.6.3                                                                                                                      
> Maven home: /usr/share/maven                                                                                                
> Java version: 1.8.0_362, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre                                                          
> Default locale: en, platform encoding: UTF-8                                                                                                            
> OS name: "linux", version: "5.15.0-1037-azure", arch: "amd64", family: "unix"

- We may need to install multiple versions of Java/Maven so we need to be very careful with the environment variables

- Let's install openjdk8 as well
```
sudo apt install openjdk-8-jdk -y
```

- Now, that we have two java versions in our system, we need to decide which one should act as a default
- So, using the following command, to set a specific java as a temporary default, we can switch between the jdk versions
```
export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH"
```

- Now, with the above 'export' command, we made openjdk-8-jdk as a temporary default for our current session in the terminal
- Which means that we can switch these java versions easily with the help of export command and all we need is the **installation path of openjdk11** to make it a default

### Jenkins Installation:

1. Execute the commands sequentiallly
  _[Jenkins Debian Packages](https://pkg.jenkins.io/debian-stable/)

1. Verify Jenkins Service
```
sudo systemctl status jenkins.service
```

1. Navigate to `http://<publicip>:8080`

2. Continue with Jenkins Installation
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

1. Copy the password & paste on Jenkins page
  -  Customize Jenkins: Install suggested plugins
  -  Getting Started:
  -  Create First Admin User:
  -  Instance Configuration: `http://<privateip>:8080/` & then Save and Finish.
  -  Jenkis is Ready: Start using Jenkins
 
2. Next login CLI to check for users
```
sudo cat /etc/passwd
```

1. A new user called as **jenkins** is created and the group name is **jenkins** with the home directory of `/var/lib/jenkins`

2. From the Jenkins UI, no matter what user you are logged in as, the low level commands are executed as a jenkins user

3. Now lets try to do `sudo apt update` from the Jenkins UI

4.  From Jenkins UI we can do anything that a linux user jenkins can do

5.  From Jenkins UI if we need to do any installations etc., we need sudo permissions without password

6.  So, Let's configure jenkins user from cli to have sudo permissions without any password prompts
```
sudo visudo
```

1.  Next, configure the **jenkins** user without password prompts
```
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
jenkins ALL=(ALL:ALL) NOPASSWD:ALL
```

For further Details _[Refer here](https://directdevops.blog/2022/05/02/devops-classroomnotes-02-may-2022/){:target="_blank"}_

![Alt text](octocat.png)
