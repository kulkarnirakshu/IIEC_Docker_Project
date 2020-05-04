# IIEC Docker Project

## Introduction:

With the changing times, new technologies are being invented. If you want to learn a new technology, you have to establish its environment first. It also takes time, we have to wait so long for setting up the new environment. Many times, we have set the environment for a specific task. Even if you want to launch an OS; however, it easily takes 1 to 2 hours. But here it can happen in just a few time. Because Docker is so fast instead of others.

Here Solomon Hykes came up with the idea of Docker where we can launch any environment is just 1 second. Docker uses containerization technology for this task. We have to set just configuration and docker will set it ready to use in just 1 second.

This project based on multi-tier architecture (If you have multiple OS, one Os providing you application & website. And this application connect to another Os to store data.) and use concept of docker-compose (Create or manage complete infrastructure as a code) to launch automatic of using a program.

## What is Docker?

Docker is a software or tool designed to make it easier to create, deploy, and run applications by using containers. Containers are isolated from one another and allow a developer to package up an application with all of the parts it needs. We can give GUI program access inside docker container.

## Environment Setup:

    Firstly installed the Virtual Box on windows.
    On the top of Virtual Box installed redhat8.
    In redhat8, installed Docker Community Edition.

## Configuration:

*change directory*
> cd /etc/yum.repos.d/

*create a file with .repo extension*
> vim docker.repo

*open docker.repo to following command*
> gedit docker.repo

*put the following code in opened file*
> [docker]
   baseurl=https://download.docker.com/linux/centos/7/x86_64/stable/
   gpgcheck=0


*After putting the above content in that file, save that file.* 

    After saving docker.repo file, run following command-

*install docker community edition*
> yum install docker-ce 

*enable docker service*
> systemctl enable docker

    Here docker setup environment is ready. For this project I need MYSQL and WORDPRESS image. Following code for installed it-
    For mysql image download:

*start docker service*
> systemctl start docker

*mysql image download*
> docker pull mysql:5.7


No alt text provided for this image

    After downloaded mysql image, set the environment variable:

No alt text provided for this image

    For wordpress image download:

*docker image download*
> docker pull wordpress:5.1.1-php7.3-apache

No alt text provided for this image

    After downloaded wordpress image, set the environment variable:

No alt text provided for this image

    Create volume for mysql and wordpress for the storage. I created volumes mysql_storage and  wp_storage respectively.

No alt text provided for this image

    Setup environment to docker-compose.

*docker-compose download*

                           
> curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-  compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose -v

 *Apply executable permissions to the binary*

 > chmod +x /usr/local/bin/docker-compose

No alt text provided for this image

    To compose the YAML:

*make directory*
> mkdir my_wordpress   

*change directory*
> cd my_wordpress

*write YAML file*

> docker-compose.yml

*open YAML file*
> gedit docker-compose.yml

No alt text provided for this image

No alt text provided for this image

    After created YAML file. Launch the configured environment in just a second from the following command-

> docker-compose up

*show containers*


> docker ps

    Using the following commands, we can direct go to in mysql command window.

*show IP*
> docker inspect 42 | grep IP

Note: Here 42 is not specific number for this command.It is first two numbers of mysql container ID.


No alt text provided for this image

    In the following command, we can use environment variable user and password.

*open mysql command window*
> mysql -h 172.17.0.2 - rakshu -predhat

     Here is mysql command window.

No alt text provided for this image

## Conclusion:

    Here is all set up environment is ready to use whenever we want to use it.
    Image is a part of script which is launch in container.
    I stored data permanent as volumes are created for mysql and wordpress, both the containers.
    We can give GUI program access inside docker.


