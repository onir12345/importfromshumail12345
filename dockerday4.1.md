


1-Create a file named index.js with below content.



shumail@shumail-Inspiron-N5110:~/index$ gedit index.js
 
shumail@shumail-Inspiron-N5110:~/index$ cat index.js 

var os = require("os");
 
var hostname = os.hostname(); 

console.log("hello from " + hostname);




2-Create a file named Dockerfile and write code as per the steps mentioned.



FROM alpine

MAINTAINER shumail <shumail.aaren@gmail.com>

RUN apk update && \
    apk add nodejs

RUN mkdir -p /app

RUN mkdir -p /shumail

COPY index.js /app

WORKDIR /app

CMD node index.js



3-Build image from docker file 


shumail@shumail-Inspiron-N5110:~/index$ docker build -t nodejs:1.0 .

Sending build context to Docker daemon  4.096kB

Step 1/8 : FROM alpine

 ---> 11cd0b38bc3c

Step 2/8 : MAINTAINER shumail <shumail.aaren@gmail.com>

 ---> Using cache

 ---> 1a46c229ad3e

Step 3/8 : RUN apk update &&     apk add nodejs

 ---> Using cache

 ---> ab19bd6f5664

Step 4/8 : RUN mkdir -p /app

 ---> Using cache

 ---> 494121877531

Step 5/8 : RUN mkdir -p /shumail

 ---> Using cache

 ---> 5a8b3e900464

Step 6/8 : COPY index.js /app

 ---> c400e698d544

Step 7/8 : WORKDIR /app

Removing intermediate container cb6d345f6277

 ---> 9503ca715c10

Step 8/8 : CMD node index.js

 ---> Running in 85854d5ee3ca

Removing intermediate container 85854d5ee3ca

 ---> 666923113f66

Successfully built 666923113f66

Successfully tagged nodejs:1.0



shumail@shumail-Inspiron-N5110:~/index$ docker images

REPOSITORY                                                      TAG                 IMAGE ID            CREATED             SIZE

nodejs                                                          1.0                 666923113f66        24 seconds ago      32.5MB



shumail@shumail-Inspiron-N5110:~$ docker run -it 666 ash
 
/app # ls -a

.         ..        index.js

/app # cat index.js

var os = require("os");
 
var hostname = os.hostname(); 

console.log("hello from " + hostname);


4-Tag image with name "hello:v0.1"


shumail@shumail-Inspiron-N5110:~$ docker tag 666 hello:v0.1

shumail@shumail-Inspiron-N5110:~$ docker images

REPOSITORY                                                      TAG                 IMAGE ID            CREATED             SIZE

nodejs                                                          1.0                 666923113f66        13 hours ago        32.5MB

hello                                                           v0.1                666923113f66        13 hours ago        32.5MB





























