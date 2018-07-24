               ASSIGNMENT 2



1-Create a DockerFile


2-Use Ubuntu latest image.


3-Add your name as a Manintainer.


4-Update local packages using command (apt-get update).


5-Install nodejs package.


6-Install npm package.


7-Create a symlink using command (ln -s /usr/bin/nodejs /usr/bin/node).


8-Trigger a command (npm install -g http-server)


9-Add any test index.html file from local at /usr/apps/hello-docker/index.html on container.


10-change your working directory to /usr/apps/hello-docker/.


11-Run a command (http-server -s) on every container initialization.




FROM ubuntu


MAINTAINER shumail <shumail.aaren@gmail.com>


RUN apt-get update && \


    apt-get install -y apt-utils && \


    apt-get install nodejs -y && \


    apt-get install npm -y


CMD ln -s /usr/bin/nodejs /usr/bin/node/


RUN npm install -g http-server


ADD index.html /usr/apps/hello-docker/index.html    


WORKDIR /usr/apps/hello-docker/


CMD http-server -s



12-Build your dockerfile and tag it with "yourname:docker-web"


shumail@shumail-Inspiron-N5110:~/maintainer$ docker build -t shumail:docker-web .



Sending build context to Docker daemon  3.072kB

Step 1/8 : FROM ubuntu

 ---> 113a43faa138


Step 2/8 : MAINTAINER shumail <shumail.aaren@gmail.com>

 ---> Using cache

 ---> 9c121e0ed379


Step 3/8 : RUN apt-get update &&     apt-get install -y apt-utils &&     apt-get install nodejs -y &&     apt-get install npm -y
 ---> Using cache

 ---> 8922baeefb6



Step 4/8 : CMD ln -s /usr/bin/nodejs /usr/bin/node/


 --> Using cache

 ---> 182e4a1915b6


Step 5/8 : RUN npm install -g http-server

 ---> Using cache

 ---> d01bf7ae0da2


Step 6/8 : ADD index.html /usr/apps/hello-docker/index.html

 ---> ca3e7ae37b26


Step 7/8 : WORKDIR /usr/apps/hello-docker/


Removing intermediate container 89ec8a59d448

 ---> 03bbe0a5199c


Step 8/8 : CMD http-server -s

 ---> Running in 34d27250c30a

Removing intermediate container 34d27250c30a

 ---> ec61dd834ac4

Successfully built ec61dd834ac4

Successfully tagged shumail:docker-web


shumail@shumail-Inspiron-N5110:~/maintainer$ docker images


REPOSITORY                                                      TAG                 IMAGE ID            CREATED              SIZE


shumail                                                         docker-web          ec61dd834ac4        About a minute ago   445MB




13-Run a docker container from the image that you have just created and map container 8080 port to host 8080 port.(8080:8080)1


shumail@shumail-Inspiron-N5110:~/maintainer$ docker run -itd -p 8080:8080 ec61


ea012dfb18fc22b49398fd92e2e8fba1f575136e3bf9e89e547409ff35f107ca


14-Try accessing your webpage using "http://<virtualmachine_ipaddress>:8080/index.html" URL.



       172.20.10.12:8080/index.html" 



15-Delete docker container and image from local.


shumail@shumail-Inspiron-N5110:~$ docker rm ea0


ea0



shumail@shumail-Inspiron-N5110:~$ docker rmi ec61

ec61











                    

