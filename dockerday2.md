         ASSIGNMENT DOCKER DAY2


         Assignment part1

1-Run A Docker Container From "Hello-World" Image.

shumail@shumail-Inspiron-N5110:~$ Docker Pull Hello-World

Using default tag: latest

latest: Pulling from library/hello-world

9db2ca6ccae0: Pull complete 

Digest: sha256:4b8ff392a12ed9ea17784bd3c9a8b1fa3299cac44aca35a85c90c5e3c7afacdc

Status: Downloaded newer image for hello-world:latest



shumail@shumail-Inspiron-N5110:~$ Docker Run Hello-World:Latest 



Hello from Docker!

This message shows that your installation appears to be working correctly.



shumail@shumail-Inspiron-N5110:~$ Docker Ps -a


CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS 

PORTS               NAMES
1c2ada69e01b        hello-world:latest   "/hello"                 30 seconds ago      Exited (0) 27 seconds ago                       elegant_albattani






2-Pull "alpine" image from docker registry and see if image is available in your local image list.

shumail@shumail-Inspiron-N5110:~$ docker pull alpine



Using default tag: latest

latest: Pulling from library/alpine

8e3ba11ec2a2: Pull complete

Digest: sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430

Status: Downloaded newer image for alpine:latest

shumail@shumail-Inspiron-N5110:~$ docker images



REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

shumailimages       1.0                 7aa1c941cdae        2 days ago          122MB

hello-world         latest              2cb0d9787c4d        5 days ago          1.85kB

nginx               latest              3c5a05123222        9 days ago          109MB

alpine              latest              11cd0b38bc3c        9 days ago          4.41MBshumail@shumail-Inspiron-
N5110:~$ docker pull alpine:3.7




3-Pull some specific version of docker "alpine" image from docker registry.


shumail@shumail-Inspiron-N5110:~$ docker pull alpine:3.7



3.7: Pulling from library/alpine

911c6d0c7995: Pull complete 

Digest: sha256:56e2f91ef15847a2b02a5a03cbfa483949d67a242c37e33ea178e3e7e01e0dfd

Status: Downloaded newer image for alpine:3.7

shumail@shumail-Inspiron-N5110:~$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

shumailimages       1.0                 7aa1c941cdae        2 days ago          122MB

hello-world         latest              2cb0d9787c4d        5 days ago          1.85kB

nginx               latest              3c5a05123222        9 days ago          109MB

alpine              latest              11cd0b38bc3c        9 days ago          4.41MB

ALPINE              3.7                 791C3E2EBFCB        9 DAYS AGO          4.2MB





4-Run a docker container from local image "alpine" and run an inline command "ls -l" while running container.


shumail@shumail-Inspiron-N5110:~$ docker run alpine ls -l


total 52

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 bin

drwxr-xr-x    5 root     root           340 Jul 16 10:33 dev

drwxr-xr-x    1 root     root          4096 Jul 16 10:33 etc

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 home

drwxr-xr-x    5 root     root          4096 Jul  5 14:47 lib

drwxr-xr-x    5 root     root          4096 Jul  5 14:47 media

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 mnt

dr-xr-xr-x  251 root     root             0 Jul 16 10:33 proc

drwx------    2 root     root          4096 Jul  5 14:47 root

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 run

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 sbin

drwxr-xr-x    2 root     root          4096 Jul  5 14:47 srv

dr-xr-xr-x   13 root     root             0 Jul 16 10:33 sys

drwxrwxrwt    2 root     root          4096 Jul  5 14:47 tmp

drwxr-xr-x    7 root     root          4096 Jul  5 14:47 usr





5-Try to take login to container created using "alpine" image.

shumail@shumail-Inspiron-N5110:~$ docker run -it alpine 



/ # ls -a

.           bin         home        mnt         run         sys         var

..          dev         lib         proc        sbin        tmp

.dockerenv  etc         media       root        srv         usr




6-Detach yourself from the container without making it exit/container kill.


By using below command you can detach yourself from container without making it exit/kill 


ctrl+p+q  .



7-Check running containers and see if you can find out the stopped containers.


shumail@shumail-Inspiron-N5110:~$ docker ps -a



CONTAINER ID        IMAGE                COMMAND                  CREATED             STATUS 

PORTS               NAMES
d14bb1f275e0        alpine               "/bin/sh"                28 seconds ago      Exited (0) 26 seconds ago 

happy_boyd
e3b861126fe3        alpine               "/bin/sh"                11 minutes ago      Up 11 minutes 

ecstatic_sinoussi
cda41b3aa071        alpine               "ls -l"                  12 minutes ago      Exited (0) 12 minutes ago

agitated_gates
b741d7c659c2        alpine               "ls -l"                  12 minutes ago      Exited (0) 12 minutes ago 

unruffled_gates
c0bd94262d28        alpine               "ls -l"                  16 minutes ago      Exited (0) 16 minutes ago

gallant_varahamihira
c84501bf1033        alpine               "/bin/sh"                16 minutes ago      Exited (0) 16 minutes ago

jolly_lamport
a9eedcf7b22b        alpine               "/bin/sh"                16 minutes ago      Exited (0) 16 minutes ago

priceless_heisenberg


here you can have outlook on status of running and stopped container.




8-Stop running container.


shumail@shumail-Inspiron-N5110:~$ docker ps



CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS 

NAMES
35a6ba49bc59        ubuntu              "/bin/bash"         28 seconds ago      Up 26 seconds  

clever_ptolemy
e3b861126fe3        alpine              "/bin/sh"           23 minutes ago      Up 23 minutes 

ecstatic_sinoussi



shumail@shumail-Inspiron-N5110:~$ docker stop 35a


35a




shumail@shumail-Inspiron-N5110:~$ docker ps 

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS 

NAMES
e3b861126fe3        alpine              "/bin/sh"           25 minutes ago      Up 25 minutes 

ecstatic_sinoussi



 

9-Start container that was stopped earlier.

shumail@shumail-Inspiron-N5110:~$ docker start 35a



35a


shumail@shumail-Inspiron-N5110:~$ docker ps 



CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS 

NAMES
35a6ba49bc59        ubuntu              "/bin/bash"         4 minutes ago       Up 6 seconds 

clever_ptolemy
e3b861126fe3        alpine              "/bin/sh"           28 minutes ago      Up 28 minutes  

ecstatic_sinoussi





10-Try to remove "alpine" image from your local system.



shumail@shumail-Inspiron-N5110:~$ docker rmi alpine


Untagged: alpine:latest

Untagged: alpine@sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430

Deleted: sha256:11cd0b38bc3ceb958ffb2f9bd70be3fb317ce7d255c8a4c3f4af30e298aa1aab

Deleted: sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c


 


                                  Assignment part2
                                  

1-Again pull "alpine" image from docker registry.


shumail@shumail-Inspiron-N5110:~$ docker pull alpine



Using default tag: latest

latest: Pulling from library/alpine

8e3ba11ec2a2: Pull complete 

Digest: sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430

Status: Downloaded newer image for alpine:latest




2-Take interactive login to bash while running docker container from "alpine" image.


shumail@shumail-Inspiron-N5110:~$ docker run -it  alpine /bin/sh


/ #


3-Run command inside container: echo "hello world" > hello.txt


/ # echo "hello world">hello.txt



/ # ls -a

.           bin         hello.txt   media       root        srv         usr

..          dev         home        mnt         run         sys         var

.dockerenv  etc         lib         proc        sbin        tmp


4-Take exit from same container without killing the container.

using command 

ctrl+P+Q




5-Run another container using below command and check if you can find hello.txt within this container. You should
find container isolations from step 3-5. docker container run alpine ls

shumail@shumail-Inspiron-N5110:~$ docker run -it  alpine /bin/sh


/ # ls -a

.           bin         home        mnt         run         sys         var

..          dev         lib         proc        sbin        tmp

.dockerenv  etc         media       root        srv         usr

  by looking both the container so we can conclude docker provide isoaltion
  
  
  

6-Stop a container using Container ID.


 
shumail@shumail-Inspiron-N5110:~$ docker ps 




CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS  

NAMES
c83c216bb6ea        alpine              "/bin/sh"           9 minutes ago       Up 9 minutes 

nervous_mendeleev
e8d45f5327a5        alpine              "/bin/sh"           12 minutes ago      Up 12 minutes 

determined_brown
35a6ba49bc59        ubuntu              "/bin/bash"         33 minutes ago      Up 29 minutes  

clever_ptolemy



shumail@shumail-Inspiron-N5110:~$ docker stop c83



c83


shumail@shumail-Inspiron-N5110:~$ docker ps 




CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS     

NAMES
e8d45f5327a5        alpine              "/bin/sh"           12 minutes ago      Up 12 minutes  

determined_brown
35a6ba49bc59        ubuntu              "/bin/bash"         34 minutes ago      Up 29 minutes 

clever_ptolemy





7-Start same container using ID and exec a command "echo 'hello world!'" in docker container without instantiating a new container.


shumail@shumail-Inspiron-N5110:~$ docker start c83


c83
shumail@shumail-Inspiron-N5110:~$ docker ps 



CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS  


NAMES
c83c216bb6ea        alpine              "/bin/sh"           11 minutes ago      Up 5 seconds 

nervous_mendeleev
e8d45f5327a5        alpine              "/bin/sh"           13 minutes ago      Up 13 minutes 

determined_brown
35a6ba49bc59        ubuntu              "/bin/bash"         35 minutes a

shumail@shumail-Inspiron-N5110:~$ docker attach c83

/ #  echo "hello world"

hello world

/ # 




8-Inspect already downloaded "alpine" docker image using docker inspect command.



shumail@shumail-Inspiron-N5110:~$ docker inspect 11c

[

    {
    
        "Id": "sha256:11cd0b38bc3ceb958ffb2f9bd70be3fb317ce7d255c8a4c3f4af30e298aa1aab",
        
        
        "RepoTags": [
        
            "alpine:latest"
            
            
        ],
        
        "RepoDigests": [
        
            "alpine@sha256:7043076348bf5040220df6ad703798fd8593a0918d06d3ce30c6c93be117e430"
            
        ],
        
        "Parent": "",
        
        "Comment": "",
        
        "Created": "2018-07-06T14:14:06.393355914Z",
        
        "Container": "b449414436d7bc63cc85dcd24abde14bcec1d92f54f2316212059ee2ed7f3a65",
        
        "ContainerConfig": {
        
        
            "Hostname": "b449414436d7",
            
            "Domainname": "",
            
            "User": "",
            
            "AttachStdin": false,
            
            "AttachStdout": false,
            
            "AttachStderr": false,
            
            "Tty": false,
            
            "OpenStdin": false,
            
            "StdinOnce": false,
            
            "Env": [
            
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
                
            ],
            
            "Cmd": [
            
                "/bin/sh",
                
                "-c",
                
                "#(nop) ",
                
                "CMD [\"/bin/sh\"]"
                
            ],
            
            "ArgsEscaped": true,
            
            "Image": "sha256:9025f4d6338c3425933e4734e8a27fb615d56ca8862e78bb8c4e2426f2db78bd",
            
            
            
            "WorkingDir": "",
            
            "Entrypoint": null,
            
            
            "OnBuild": null,
            
            
            "Labels": {}
            
        },
        
        "DockerVersion": "17.06.2-ce",
        
        "Author": "",
        
        "Config": {
        
            "Hostname": "",
            
            "Domainname": "",
            
            
            "User": "",
            
            "AttachStdin": false,
            
            "AttachStdout": false,
            
            "AttachStderr": false,
            
            
            "Tty": false,
            
            "OpenStdin": false,
            
            "StdinOnce": false,
            
            
            "Env": [
            
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
                
            ],
            
            "Cmd": [
            
                "/bin/sh"
                
            ],
            
            "ArgsEscaped": true,
            
            "Image": "sha256:9025f4d6338c3425933e4734e8a27fb615d56ca8862e78bb8c4e2426f2db78bd",
            
            "Volumes": null,
            
            "WorkingDir": "",
            
            "Entrypoint": null,
            
            "OnBuild": null,
            
            "Labels": null
            
        },
        
        "Architecture": "amd64",
        
        "Os": "linux",
        
        "Size": 4413370,
        
        "VirtualSize": 4413370,
        
        "GraphDriver": {
        
            "Data": {
            
                "MergedDir": "/var/lib/docker/overlay2
                
                /de33b35ce81359579b1490f187162c0d92a8668a20162d0dac029967f939e0b7/merged",
                
                "UpperDir": "/var/lib/docker/overlay2
                
                /de33b35ce81359579b1490f187162c0d92a8668a20162d0dac029967f939e0b7/diff",
                
                "WorkDir": "/var/lib/docker/overlay2
                
                /de33b35ce81359579b1490f187162c0d92a8668a20162d0dac029967f939e0b7/work"
                
            },
            "Name": "overlay2"
            
        },
        
        "RootFS": {
        
            "Type": "layers",
            
            "Layers": [
            
                "sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c"
                
            ]
        },
        
        
        
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]






9-Tag your local "alpine" image with name "myimage" along with version 1.0


shumail@shumail-Inspiron-N5110:~$ docker tag alpine myimage:1.0



shumail@shumail-Inspiron-N5110:~$ docker images



REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

shumailimages       1.0                 7aa1c941cdae        3 days ago          122MB

hello-world         latest              2cb0d9787c4d        6 days ago          1.85kB

nginx               latest              3c5a05123222        10 days ago         109MB

ALPINE              LATEST              11CD0B38BC3C        10 DAYS AGO         4.41MB

MYIMAGE             1.0                 11CD0B38BC3C        10 DAYS AGO         4.41MB









