# Spring PetClinic Sample Application [![Build Status](https://travis-ci.org/spring-projects/spring-petclinic.png?branch=master)](https://travis-ci.org/spring-projects/spring-petclinic/)
Deploy this sample application to Pivotal Web Services:

<a href="https://push-to.cfapps.io?repo=https%3A%2F%2Fgithub.com%2Fspring-projects%2Fspring-petclinic.git">
    <img src="https://push-to.cfapps.io/ui/assets/images/Push-to-Pivotal-Light-with-Shadow.svg" width="180" alt="Push" align="center">
</a>

## Understanding the Spring Petclinic application with a few diagrams
<a href="https://speakerdeck.com/michaelisvy/spring-petclinic-sample-application">See the presentation here</a>

## Running petclinic locally
Petclinic is a [Spring Boot](https://spring.io/guides/gs/spring-boot) application built using [Maven](https://spring.io/guides/gs/maven/). You can build a jar file and run it from the command line:


```
git clone https://github.com/spring-projects/spring-petclinic.git
cd spring-petclinic
./mvnw package
java -jar target/*.jar
```

You can then access petclinic here: http://localhost:8080/

<img width="1042" alt="petclinic-screenshot" src="https://cloud.githubusercontent.com/assets/838318/19727082/2aee6d6c-9b8e-11e6-81fe-e889a5ddfded.png">

You can find rest of the information about this spring-boot app can be found in this repository.
Credits ---> https://github.com/spring-projects/spring-petclinic.git


I have compared containerizing this application with Docker ( using multi stage Docker file ) and using Google cloud Jib method 
Jib -----> https://github.com/GoogleContainerTools/jib

You can see this video to know more about jib (https://www.youtube.com/watch?v=H6gR_Cv4yWI)

This is exclusively working for a GCP environment since its using GCR for helper images, planing to make it available it as a library so that everyone can use it..

Here i'm using maven to build this app ( u can also use gradle as well )

You need to add this plugin to the pom.xml, replace the container registry space
------------------------------------------------------------------------------------

<plugin>
  <groupId>com.google.cloud.tools</groupId>
  <artifactId>jib-maven-plugin</artifactId>
  <version>0.9.0</version>
  <configuration>
    <to>
      <image>gcr.io/Your_project_ID_goes_here/image-built-with-jib</image>
    </to>
  </configuration>
</plugin>
---------------------------------------------------------------------


Then run ( this will build the app using distroless base image and containerize this app and also push it to the given registry )

mvn compile jib:build   


-------------------------------------------------------------------------
Image built with jib 

Image build using multistage docker file
