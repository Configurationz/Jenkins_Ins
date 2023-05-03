
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

### Jenkins 
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
