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
- [CUP] (http://www.inocybe.com/2014/11/26/md-sal-cup-example-tutorial/)
- [toaster] (https://wiki.opendaylight.org/view/OpenDaylight_Controller:MD-SAL:Toaster_Step-By-Step)
- [toaster (china) ] (http://blog.csdn.net/aaa_aa000/article/details/45840977)

# step guide
```
1. Confirm start
https://wiki.opendaylight.org/view/Controller_Core_Functionality_Tutorials:Application_Development_Tutorial

    impl/src/main/java/org/opendaylight/hello/impl/HelloProvider.java
    In the HelloProvider.onSessionInitiate method:

    @Override
    public void onSessionInitiated(ProviderContext session) {
        LOG.info("HelloProvider Session Initiated");
    }
2. Modify yang
Edit

 api/src/main/yang/hello.yang
 Edit this file to look as below. You will see that we are adding the code in a YANG module to define the 'hello-world' RPC:

 module hello {
  yang-version 1;
  namespace "urn:opendaylight:params:xml:ns:yang:hello";
  prefix "hello";

  revision "2015-01-05" {
   description "Initial revision of hello model";
  }
  rpc hello-world {
   input {
    leaf name {
     type string;
    }
   }
   output {
    leaf greeting {
     type string;
    }
   }
  }
 }
```
