# docker_project_on-_wordpress
Under the guidance of Vimal Daga sir,I have learnt docker from begineer to expertise level.From that knowledge I have created a project using docker container.
##EXlpanation of Project:
In this project,I have create two containers first is mysql database and second is wordpress where we can post our blogs and articles.I have linked the wordpress to mysql.
Through docker-compose file of my project anyone can setup wordpress in very simple steps.
##Environment:
###1.Pre-configurations needed:
 I am using RedHat8 IN Virtual Machine and docker is installed in it.You can use any O.S as base but it should docker software installed.
  *Disable firewall:
   Some times firewall might conflict with network connection of docker.
   use `system stop firewalld` .
  *start docker :
   use `systemctl start docker`.
  *
  *mysql client software :
  we required a client software for accessing our database.
  In RHEL8 use `yum install mysql`.
 
###2.Docker Images:
  we need two docker images for setting up the envirnment.
  *1.mysql image :
  use `docker pull mysql:5.7` command to download mysql database.We are using my  sql 5.7 version as it is more compartiable with our given wordpress version.we  are pulling images from official page of docker:https://hub.docker.com/_/mysql 
  *2.wordpress images:
  use `docker pull wordpress:5.1.1-php7.3-apache`
  To know more about this wordpress images you can read here:https://hub.docker.com/_/wordpress
##Docker Compose:
You have to first install docker-compose in your system .you install it from given link:https://docs.docker.com/compose/install/
for linux directly use this command `sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`.
###My docker compose file:


 *####version:In every yml file we have to specify version,here we are using version 3 of docker compose.
 *####services:This section specify the services we are using through docker compose.
 *####Container name:dbos and wpos are the name of our conatiner.
 *####images:This specify the docker images we our using for setup.
 *####restart:Due to any reason if any of the container stops docker-compose will again restart it.
 *###Volumes:In docker as soon as we terminate an container our whole data inside that container destroyed. But if we want to make our data permanent then we have to use docker volume.
 *####environmrnt:we need to pass some information some pre-define environment variable that are required setup like username ,passsword,etc.
 *####depends_on:wordpress needs MySQL database server to store there files that's why we are using depends_on.
 *####Ports:for exposing our website to the outside world so that they can can access of page therefore we have to give port number.

##Sets to setup wordpress:
 
 ###step1:download the docker-compose.yml file the above repository and go the same folder where you have downloaded this file.


 ###step2:open this file using following command `vi docker-compose.yml` and changes the environment like root password ,user name,etc.
 save the changes using `esc + x`.
 ###step3:Now run `docker compose up` command and this will setup all services.


 ###step4: open browser and enter your ip address of base from where you you run docker command with 8085 port number.



 **FINALLY you can see wordpress running successfully**

 #### For closing use this command : `docker compose down` in new terminal..


