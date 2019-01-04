<center><p align="center"><img src="docimg/jbpm_logo.png">&nbsp;+&nbsp;<img src="docimg/gradle_logo.png"></p></center>

jBPM Business Applications - Gradle Build
--------------------
[Gradle](https://gradle.org/)build files for [jBPM Business Applications](http://jbpm.org/businessapps/gettingStarted.html) generated via

**[start.jbpm.org](http://start.jbpm.org)**

Why is this needed
--------------------
By default generated jBPM Business Applications are built with Apache Maven.
This gives the ability for Gradle users to build and launch your jBPM business apps.

Prerequisites:
--------------------
1. Generate your jBPM Business Application via **[start.jbpm.org](http://start.jbpm.org)**
2. Make sure you have Gradle installed. For more info visit **https://gradle.org/install/**.

Using Gradle build files:
--------------------

build.gradle and settings.gradle
--------------------
Independent of your OS, these two file need to be added 
to your jBPM Business Application **service module** root directory.

Before you can start using **build.gradle**, set the following info to the same 
ones used in your pom.xml file of the service module.

So below, replace **KIE_VERSION**, **GROUP_ID**, **ARTIFACT_ID**, and **VERSION** 
with the same defined in pom.xml:
```
kieVersion = 'KIE_VERSION'
my_groupId = 'GROUP_ID'
my_artifactId = 'ARTIFACT_ID'
my_version = 'VERSION'
```

Before you can start using **settings.gradle**. set the artifactId to the same
as defined in your pom.xml file of the service module.

So below, replace **ARTIFACT_ID** with the same defined in pom.xml:
```
rootProject.name = 'ARTIFACT_ID'
```

With these two small changes you can now build your **service module** with
the following command:

```
gradle build install
```

and start your jBPM business app with:

```
java -jar build/libs/YOUR_APP_NAME-VERSION.jar
```
where **YOUR_APP_NAME-VERSION** is the actual name of the jar file generated 
for your business application, so for example:
```
java -jar build/lib/business-application-service-1.0-SNAPSHOT.jar
```
Note that this build script will only build your **service module**. In order 
to build your business apps **kjar** and **model** modules and start your
app automatically, you will also need the build scripts described below.


Build scripts (Unix OSX Windows)
--------------------
Depending on your OS you will need to copy the below described build scripts to your 
**service module** of the jBPM business app:

1. **gradle.sh** (Unix / OSX)
2. **gradle-dev.sh** (Unix / OSX)
3. **gradle.bat** (Windows)
4. **gradle-dev.bat** (Windows)

These scripts will build your entire business app (the kjar, model, and service modules), as well
as start it for you (note the -dev scripts will launch your app in dev mode). So for example:

```
./gradle.sh build install
```
for Unix / OSX or:
```
gradle.bat build install
```
for Windows