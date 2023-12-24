### Base image ###
FROM redhat/ubi8

### Install the required packages required for Django ###
RUN  yum install python3 -y
RUN  pip-3 install django

### Create the default working directory ###
RUN  mkdir /var/hello-project
WORKDIR /var/hello-project

### Start Django Project ###
RUN  django-admin startproject Hello
WORKDIR /var/hello-project/Hello

### Expose the container on port 8000 ###
EXPOSE 8000

### Start the server when the container start ###
CMD  python3 manage.py runserver 0.0.0.0:8000
