# Chatbot-for-Social-Engineering
Project for program development UoG Master

This is the user guide for telling you how to install relevant application for this Chatbot and the setps for running and using it.

The Chatbot was build based on JAVA enviroment and using Spring Boot structure as a maven project.

Thus, Project deployment is generally in two ways: one is to package it into a jar package and execute it directly, the other is to package it into a war package and put it under the tomcat server. Springboot generally defaults to jar package, here I record both jar package and war package.

1. Jar package method:

a. Clean it up with mvn clean first;

b. Ignore the test class and type the jar package command: mvn clean package -Dmaven.test.skip=true;

c. After uploading the jar package to the server, use the command: nohup java -jar target/spring-boot-scheduler-1.0.0.jar & start the service to access it normally.

2. War package method:

a. Change <packaging>jar</packaging> under pom to <packaging>war</packaging>

b. Modify under pom --- Exclude the built-in tomcat when packaging

c. Set the scope attribute to provided, so that this JAR package will not be included in the final WAR, because servers such as Tomcat or Jetty will provide related API classes at runtime.

d. Register the startup class

Create ServletInitializer.java, inherit SpringBootServletInitializer, override configure(), and register the startup class Application. When the external Web application server constructs the Web Application Context, the startup class will be added.

e. Execute mvn clean package -Dmaven.test.skip=true to ignore the test class, package and upload it to the server, start tomcat and you can access it!
