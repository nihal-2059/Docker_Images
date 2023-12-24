## Base Image on which the jenkins would be installed ##
FROM redhat/ubi8

## Multiple softwares to be installed ##
RUN  yum install wget sudo git -y

## Get the repo and the gpg keys for Jenkins ##
RUN  wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo && rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

## Install Java and Jenkins ##
RUN  yum upgrade -y
RUN  yum install java-17-openjdk jenkins -y

## Create the directory and set the required permissions ##
RUN mkdir -p /var/jenkins_home && chown jenkins:jenkins /var/jenkins_home

## Update the home directory for jenkins ##
ENV JENKINS_HOME=/var/jenkins_home

## Copy the script to start jenkins inside Container ##
ADD  script.sh /usr/local/bin/script.sh
RUN  chmod +x /usr/local/bin/script.sh

## Expose the port on which Jenkins will listen ##
EXPOSE 8080/tcp

## Set the user to run the scripts and overall jenkins ##
USER jenkins

## Start jenkins using the script ##
ENTRYPOINT /usr/local/bin/script.sh

