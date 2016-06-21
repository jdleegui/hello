# hello

## [HELLO] (https://wiki.opendaylight.org/view/Controller_Core_Functionality_Tutorials:Application_Development_Tutorial)
### https://wiki.opendaylight.org/view/Controller_Core_Functionality_Tutorials:Application_Development_Tutorial

```
echo "# hello" >> README.md
git init
git add README.md
git commit -m "hello commit"
git remote add origin https://github.com/jdleegui/hello.git
git push -u origin master 

```
- [x] Make a project
```
mvn archetype:generate -DarchetypeGroupId=org.opendaylight.controller \
-DarchetypeArtifactId=opendaylight-startup-archetype \
-DarchetypeVersion=1.2.0-SNAPSHOT \
-DarchetypeRepository=http://nexus.opendaylight.org/content/repositories/opendaylight.snapshot/ \
-DarchetypeCatalog=http://nexus.opendaylight.org/content/repositories/opendaylight.snapshot/archetype-catalog.xml

Define value for property 'groupId': : org.opendaylight.hello
Define value for property 'artifactId': : hello
Define value for property 'package':  org.opendaylight.hello: : 
Define value for property 'classPrefix':  Hello: : 
Define value for property 'copyright': : Yoyodyne, Inc.
```
- [x] compile and run
```
cd hello
mvn clean install -DskipTests
./karaf/target/assembly/bin/karaf 
localhost:8080/index.html
```
- [x] Add simple RPC
[CUP] (http://www.inocybe.com/2014/11/26/md-sal-cup-example-tutorial/)
