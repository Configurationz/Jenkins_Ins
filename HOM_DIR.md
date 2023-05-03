
### JAVA_HOME
```
/usr/lib/jvm/java-11-openjdk-amd64/
```

### Maven home:
```
/usr/share/maven
```
* Maven will download all the necessary dependencies to compile/test/package from a maven central repository [Refer Here](https://mvnrepository.com/repos/central) 
  and it downloads to `M2_HOME` which is by default `<HOME-DIR>/.m2` which is referred as local repository.

* Compile the code: `mvn compile`
* Run the Automated tests: `mvn test`
* Create the package: `mvn package`

### JENKINS_HOME
* Jenkins user's home directory
```
/var/lib/jenkins
```
* Firstly, become a root user as we can login any user being a superuser.
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

* Extra
  * Whatever the configuration we do on Jenkins UI, everything get's stored in Jenkin's server i.e., cli as pom.xml file.
  * After cloning from any repository, the whole repository gets cloned with all the files & folders in workspace directory.
  * When we build a project, jenkins creates a folder with project's name in workspace folder, this folder is referred as workspace for the job.
  * How to preserve the data of Jenkins ?
  * Take backup of `/var/lib/jenkins` folder frequently because jenkins stores everything in it's home directory.

* Jenkins has two types of Nodes -
  * __Master Node__: This is the node where we install jenkins.
  * __Node__: This is the node on which we can run the job which matches the label definition.







