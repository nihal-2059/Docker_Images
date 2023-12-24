### build image using redhat as base image ###
FROM redhat/ubi8

### Create the required directory for tomcat ###
RUN mkdir -p /opt/tomcat

### Switch to the tomcat home directory ###
WORKDIR /opt/tomcat

### Install the required packages ###
RUN yum install wget java-17-openjdk -y 

### get the required packages and unarchive the file ###
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.78/bin/apache-tomcat-9.0.78.tar.gz && tar xzf apache-tomcat-9.0.78.tar.gz

### Set the required environmental variables ###
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-17.0.8.0.7-2.el8.aarch64 
ENV CATALINA_HOME=/opt/tomcat/apache-tomcat-9.0.78

### Expose the tomcat service ###
EXPOSE 8080

### Start the tomcat service ###
CMD ["/opt/tomcat/apache-tomcat-9.0.78/bin/catalina.sh","run"]

