# docker-grails-war-deployment
In this repo we shall have steps to deploy grails and groovy application war.

## Set-up environment
- `Java 7`
- `Grails 2.X`
- `Docker-for-windows`
- `Apache-tomcat-7x`

## Description of dockerfile in this repo . 


  `FROM java:7` :  refers to what we base our current docker image with. In our case , Java 7 it is.
  
  `MAINTAINER`  :  Name of the deployer/maintainer

  `RUN`         :  Typically requires archive/install location for the packages/libraries our application depends on.
  
  `ADD`         :  Copies files(in our case the .war file) from local host machine to MobyLinuxVM'a tomcat .
                   Ex. FTP-0.1.war apache-tomcat-7.0.55/webapps/

  `CMD`         :  Command the docker daemon to run the application using apache-tomcat-7.0.55/bin/startup.sh && tail -f apache-tomcat-           
                   7.0.55/logs/catalina.out

  `EXPOSE`      :  Mention the port tomcat instance would run.


## Build the docker image 

    Traverse to the folder containing dockerfile( if necessary according to the path for .war, this folder can containe .war to be deployed)
  
    ` docker build -t name-of-image .`
    
     - Eg : docker build -t grails-application-tomcat-im
     
##  Run the docker image 

    `docker run name-of-image`
    
     - Eg : docker run  grails-application-tomcat-im
