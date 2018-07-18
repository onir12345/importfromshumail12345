       ASSIGNMENT DOCKER DAY3



1- Pull nginx image from dockerhub


shumail@shumail-Inspiron-N5110:~$ docker pull nginx


Using default tag: latest


latest: Pulling from library/nginx


Digest: sha256:a65beb8c90a08b22a9ff6


a219c2f363e16c477b6d610da28fe9cba37c2c3a2ac


Status: Image is up to date for nginx:latest







2-Run a container from nginx image and map container port 80 to system port 80.


shumail@shumail-Inspiron-N5110:~$ docker run -it -p 80:80 nginx bash


root@cb7638838aaf:/# 


CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS                NAMES


cb7638838aaf        nginx               "bash"              About a minute ago   Up About a minute 


0.0.0.0:80->80/tcp   brave_turing


shumail@shumail-Inspiron-N5110:~$ docker exec -it brave_turing bash


root@cb7638838aaf:/# service nginx status


[FAIL] nginx is not running ... failed!


root@cb7638838aaf:/# service nginx start 


root@cb7638838aaf:/# 

192.168.0.67 - - [18/Jul/2018:06:01:52 +0000] "GET / HTTP/1.1" 200 612 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64
;

 rv:60.0) Gecko/20100101 Firefox/60.0" "-"
 
 
 
 
 
 
 




3-Display all mapped ports on nginx image.



shumail@shumail-Inspiron-N5110:~$ docker port cb7


80/tcp -> 0.0.0.0:80







4-Run a docker container named "containexpose" from nginx image and expose port 80 of container to outer world 



without mapping it to any of


 system port.
 

shumail@shumail-Inspiron-N5110:~$ docker run -itd --network host --name nginx nginx


94d9bc308a37c582a4ecd3b9547529e75e623ee24b37e8af0f4bdb8185a22463




Docker Volume:





1-Create docker volume named "dbvol"




shumail@shumail-Inspiron-N5110:~$ docker volume create dbvol 




dbvol









2-Run docker container from wordpress image and mount "dbvol" to /var/lib/mysql



shumail@shumail-Inspiron-N5110:~$ docker run -it --name wordpress -v dbvol:/var/lib/mysql wordpress bash


root@279189d1a822:/var/www/html# 







3-Display all docker volumes.



shumail@shumail-Inspiron-N5110:~$ docker volume ls



DRIVER              VOLUME NAME



local               5459c14f04752e7d86f9839cbbd60730ac3168680d420de22f414a0fcdc419c9



local               dbvol








4-Create another docker volume named "testvol"


shumail@shumail-Inspiron-N5110:~$ docker volume create testvol


testvol


shumail@shumail-Inspiron-N5110:~$ docker volume ls 


DRIVER              VOLUME NAME


local               5459c14f04752e7d86f9839cbbd60730ac3168680d420de22f414a0fcdc419c9


local               dbvol


local               testvol








 

5-Remove docker volume "testvol"


shumail@shumail-Inspiron-N5110:~$ docker volume rm testvol


testvol



shumail@shumail-Inspiron-N5110:~$ docker volume ls 


DRIVER              VOLUME NAME


local               5459c14f04752e7d86f9839cbbd60730ac3168680d420de22f414a0fcdc419c9


local               dbvol





Docker Linking:






1-Run a container in detached mode with name "db" from image "training/postgres"



shumail@shumail-Inspiron-N5110:~$ docker run -itd  --name db training/postgres


Unable to find image 'training/postgres:latest' locally


latest: Pulling from training/postgres


a3ed95caeb02: Pull complete 


6e71c809542e: Already exists 


2978d9af87ba: Pull complete 


e1bca35b062f: Pull complete 


500b6decf741: Pull complete

 
74b14ef2151f: Pull complete 


7afd5ed3826e: Pull complete 


3c69bb244f5e: Pull complete 


d86f9ec5aedf: Pull complete 


010fabf20157: Pull complete 


Digest: sha256:a945dc6dcfbc8d009c3d972931608344b76c2870ce796da00a827bd50791907e


Status: Downloaded newer image for training/postgres:latest


3b6e34816b78c8f220ee62f51c33c6856080dce73aa45eb6c02be3e817f95eb2








2-Run another container in detached mode with name "web" from image "training/webapp", link container "db" with 


alias "mydb" to this container and finally pass an inline command "python app.py" while running container.





shumail@shumail-Inspiron-N5110:~$ docker run -itd --name web --link db:mydb  training/webapp 


Unable to find image 'training/webapp:latest' locally


latest: Pulling from training/webapp


e190868d63f8: Pull complete 


0b9bfabab7c1: Pull complete 


a3ed95caeb02: Pull complete 


10bbbc0fc0ff: Pull complete 


fca59b508e9f: Pull complete 


e7ae2541b15b: Pull complete

 
9dd97ef58ce9: Pull complete 


a4c1b0cb7af7: Pull complete 


Digest: sha256:06e9c1983bd6d5db5fba376ccd63bfa529e8d02f23d5079b8f74a616308fb11d


Status: Downloaded newer image for training/webapp:latest


0f1f2de8259083181bbd7ffc19a15277a52e618d04502e4585cdc85ae1066c62








3-Take a bash terminal in "web" container.



shumail@shumail-Inspiron-N5110:~$ docker exec -it web /bin/sh



#









4-Test container linking by doing a ping to "mydb"


# ping mydb


PING mydb (172.17.0.3) 56(84) bytes of data.


64 bytes from mydb (172.17.0.3): icmp_seq=1 ttl=64 time=0.287 ms


64 bytes from mydb (172.17.0.3): icmp_seq=2 ttl=64 time=0.149 ms


64 bytes from mydb (172.17.0.3): icmp_seq=3 ttl=64 time=0.148 ms



64 bytes from mydb (172.17.0.3): icmp_seq=4 ttl=64 time=0.148 ms


64 bytes from mydb (172.17.0.3): icmp_seq=5 ttl=64 time=0.152 ms


64 bytes from mydb (172.17.0.3): icmp_seq=6 ttl=64 time=0.124 ms


64 bytes from mydb (172.17.0.3): icmp_seq=7 ttl=64 time=0.148 ms


64 bytes from mydb (172.17.0.3): icmp_seq=8 ttl=64 time=0.155 ms


64 bytes from mydb (172.17.0.3): icmp_seq=9 ttl=64 time=0.137 ms


64 bytes from mydb (172.17.0.3): icmp_seq=10 ttl=64 time=0.160 ms


^C
--- mydb ping statistics ---


10 packets transmitted, 10 received, 0% packet loss, time 9221ms




rtt min/avg/max/mdev = 0.124/0.160/0.287/0.046 ms










