## BASE IMAGE ##
FROM redhat/ubi8

## Install Pre-Requisite packages ##
RUN yum install -y java-1.8.0-openjdk git maven wget

## Set environment variable JAVA_HOME ##
ENV JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.392.b08-4.el8.aarch64/jre
ENV PATH=$PATH:/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.392.b08-4.el8.aarch64/jre/bin

## Create necessary directory for bamboo installation and working directory ##
RUN mkdir /root/bamboo /root/bamboo-home

## Download binaries for Bamboo ##
WORKDIR /root/bamboo
RUN wget https://product-downloads.atlassian.com/software/bamboo/downloads/atlassian-bamboo-7.0.2.tar.gz

## Extract and the required files ##
RUN tar -xf atlassian-bamboo-7.0.2.tar.gz

## Update the home directory for bamboo ##
RUN echo bamboo.home=/root/bamboo-home > atlassian-bamboo-7.0.2/atlassian-bamboo/WEB-INF/classes/bamboo-init.properties

## Open required ports for Bamboo ##
EXPOSE 8085

## Copy startup script to the image ##
ADD script.sh /usr/local/bin/script.sh
RUN chmod +x /usr/local/bin/script.sh

## Start the bamboo server ##
ENTRYPOINT /usr/local/bin/script.sh
