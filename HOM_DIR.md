
### JAVA_HOME

[OpenLogic](https://www.openlogic.com/openjdk-downloads)

[Microsoft Build of OpenJDK](https://learn.microsoft.com/en-us/java/openjdk/download)

[Red Hat build of OpenJDK](https://developers.redhat.com/products/openjdk/download)

[Archived OpenJDK General-Availability Releases](https://jdk.java.net/archive/)

[AdoptOpenJDK / openjdk11-binaries _(GitHub)_](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases)

[Prebuilt OpenJDK packages _(official documentation)_](https://openjdk.org/install/)

* We'll be looking for Java 11 installed in Ubuntu Distribution, using following commands.
```
whereis java
```
> java: /usr/bin/java /usr/share/java /usr/share/man/man1/java.1.gz

```
ls -al /usr/bin/java
```
> lrwxrwxrwx 1 root root 22 Jul  3 08:39 /usr/bin/java -> /etc/alternatives/java

```
ls -al /etc/alternatives/java
```
> lrwxrwxrwx 1 root root 43 Jul  3 08:39 /etc/alternatives/java -> /usr/lib/jvm/java-11-openjdk-amd64/bin/java

```
/usr/lib/jvm/java-11-openjdk-amd64/bin/java -version
```
> openjdk version "11.0.19" 2023-04-18                                                                                                                                                      
> OpenJDK Runtime Environment (build 11.0.19+7-post-Ubuntu-0ubuntu120.04.1)                                                                                
> OpenJDK 64-Bit Server VM (build 11.0.19+7-post-Ubuntu-0ubuntu120.04.1, mixed mode, sharing)

  * So, according to above conclusion, the path for Java Home Directory is *__```/usr/lib/jvm/java-11-openjdk-amd64/```__*

* Now, Follow the same steps for RedHat/CentOS
```
whereis java
```
> java: /usr/bin/java /usr/lib/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz

```
ls -al /usr/bin/java
```
> lrwxrwxrwx. 1 root root 22 Jul  5 02:25 /usr/bin/java -> /etc/alternatives/java

```
ls -al /etc/alternatives/java
```
> lrwxrwxrwx. 1 root root 62 Jul  5 02:25 /etc/alternatives/java -> /usr/lib/jvm/java-11-openjdk-11.0.19.0.7-4.el8.x86_64/bin/java

```
/usr/lib/jvm/java-11-openjdk-11.0.19.0.7-4.el8.x86_64/bin/java -version
```
> openjdk version "11.0.19" 2023-04-18 LTS                                                                                                                                          
> OpenJDK Runtime Environment (Red_Hat-11.0.19.0.7-2) (build 11.0.19+7-LTS)                                                                                                
> OpenJDK 64-Bit Server VM (Red_Hat-11.0.19.0.7-2) (build 11.0.19+7-LTS, mixed mode, sharing)

* So, here, the path for Java Home Directory is *__```/usr/lib/jvm/java-11-openjdk-11.0.19.0.7-4.el8.x86_64/```__*

  * But, in some scenarios for RedHat/CentOS m/c, the java home directory's file path could be following as well
```
/usr/lib/jvm/jre/bin/java -version
```
> openjdk version "11.0.19" 2023-04-18 LTS                                                                                                                                          
> OpenJDK Runtime Environment (Red_Hat-11.0.19.0.7-2) (build 11.0.19+7-LTS)                                                                                                
> OpenJDK 64-Bit Server VM (Red_Hat-11.0.19.0.7-2) (build 11.0.19+7-LTS, mixed mode, sharing)

### Maven home
```
/usr/share/maven
```
* Maven will download all the necessary dependencies to compile/test/package from a maven [central repository](https://mvnrepository.com/repos/central) 
  and it downloads to `M2_HOME` which is by default `<HOME-DIR>/.m2` which is referred as local repository.

* Compile the code: `mvn compile`
* Run the Automated tests: `mvn test`
* Create the package: `mvn package`

### JENKINS_HOME
* Jenkins user's home directory
```
/var/lib/jenkins
```
* To verify, become a root user as we can login any user being a superuser.
```
sudo -i
```
```
su jenkins
```
```
pwd
```
>/var/lib/jenkins

[Official Jenkins LTS versions](https://www.jenkins.io/doc/book/installing/linux/)
* Extra
  * Whatever the configuration we do on Jenkins UI, everything get's stored in Jenkin's server i.e., cli as pom.xml file.
  * After cloning from any repository, the whole repository gets cloned with all the files & folders in workspace directory.
  * When we build a project, jenkins creates a folder with project's name in workspace folder, this folder is referred as workspace for the job.
  * How to preserve the data of Jenkins ?
  * Take backup of `/var/lib/jenkins` folder frequently because jenkins stores everything in it's home directory.

* Jenkins has two types of Nodes -
  * __Master Node__: This is the node where we install jenkins.
  * __Node__: This is the node on which we can run the job which matches the label definition.
* Adding more Nodes increases number of executors per server which means we can build more projects.





