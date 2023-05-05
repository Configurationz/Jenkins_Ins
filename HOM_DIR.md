
### JAVA_HOME
```
/usr/lib/jvm/java-11-openjdk-amd64/
```
[OpenLogic](https://www.openlogic.com/openjdk-downloads)

[Microsoft Build of OpenJDK](https://learn.microsoft.com/en-us/java/openjdk/download)

[Red Hat build of OpenJDK](https://developers.redhat.com/products/openjdk/download)

[Archived OpenJDK General-Availability Releases](https://jdk.java.net/archive/)

[AdoptOpenJDK / openjdk11-binaries _(GitHub)_](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases)

[Prebuilt OpenJDK packages _(official documentation)_](https://openjdk.org/install/)

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





