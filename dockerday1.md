         Assignment Docker Day1





1- SCRIPT TO INSTALL DOCKER 'CURL -FSSL HTTPS://GET.DOCKER.COM/ | SH' 



[vagrant@localhost ~]$ curl -fsSL https://get.docker.com/ | sh




# Executing docker install script, commit: 36b78b2
+ sudo -E sh -c 'yum install -y -q yum-utils'
Package yum-utils-1.1.31-45.el7.noarch already installed and latest version
+ sudo -E sh -c 'yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo'
Loaded plugins: fastestmirror
adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
grabbing file https://download.docker.com/linux/centos/docker-ce.repo to /etc/yum.repos.d/docker-ce.repo
repo saved to /etc/yum.repos.d/docker-ce.repo
+ '[' edge '!=' stable ']'
+ sudo -E sh -c 'yum-config-manager --enable docker-ce-edge'
Loaded plugins: fastestmirror
============================= repo: docker-ce-edge =============================
[docker-ce-edge]
async = True
bandwidth = 0
base_persistdir = /var/lib/yum/repos/x86_64/7
baseurl = https://download.docker.com/linux/centos/7/x86_64/edge
cache = 0
cachedir = /var/cache/yum/x86_64/7/docker-ce-edge
check_config_file_age = True
compare_providers_priority = 80
cost = 1000
deltarpm_metadata_percentage = 100
deltarpm_percentage = 
enabled = 1
enablegroups = True
exclude = 
failovermethod = priority
ftp_disable_epsv = False
gpgcadir = /var/lib/yum/repos/x86_64/7/docker-ce-edge/gpgcadir
gpgcakey = 
gpgcheck = True
gpgdir = /var/lib/yum/repos/x86_64/7/docker-ce-edge/gpgdir
gpgkey = https://download.docker.com/linux/centos/gpg
hdrdir = /var/cache/yum/x86_64/7/docker-ce-edge/headers
http_caching = all
includepkgs = 
ip_resolve = 
keepalive = True
keepcache = False
mddownloadpolicy = sqlite
mdpolicy = group:small
mediaid = 
metadata_expire = 21600
metadata_expire_filter = read-only:present
metalink = 
minrate = 0
mirrorlist = 
mirrorlist_expire = 86400
name = Docker CE Edge - x86_64
old_base_cache_dir = 
password = 
persistdir = /var/lib/yum/repos/x86_64/7/docker-ce-edge
pkgdir = /var/cache/yum/x86_64/7/docker-ce-edge/packages
proxy = False
proxy_dict = 
proxy_password = 
proxy_username = 
repo_gpgcheck = False
retries = 10
skip_if_unavailable = False
ssl_check_cert_permissions = True
sslcacert = 
sslclientcert = 
sslclientkey = 
sslverify = True
throttle = 0
timeout = 30.0
ui_id = docker-ce-edge/x86_64
ui_repoid_vars = releasever,











2-START DOCKER SERVICE AND CHECK STATUS OF THE SAME.


[vagrant@localhost ~]$ sudo systemctl status docker 



● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: inactive (dead)
     Docs: https://docs.docker.com
     
     
[vagrant@localhost ~]$ sudo systemctl start docker 



[vagrant@localhost ~]$ sudo systemctl status docker



● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2018-07-17 18:46:20 +08; 3s ago
     Docs: https://docs.docker.com
 Main PID: 3185 (dockerd)
    Tasks: 16
   Memory: 37.3M
   CGroup: /system.slice/docker.service
           ├─3185 /usr/bin/dockerd
           └─3189 docker-containerd --config /var/run/docker/containerd/conta...










3-ENABLE DOCKER SERVICE TO START AT EVERY MACHINE REBOOT.

[vagrant@localhost ~]$ sudo systemctl enable docker











4-DISPLAY DOCKER VERSION.

[vagrant@localhost ~]$ docker version
Client:

 Version:      18.05.0-ce
 
 API version:  1.37
 
 Go version:   go1.9.5
 
 Git commit:   f150324
 
 Built:        Wed May  9 22:14:54 2018
 
 OS/Arch:      linux/amd64
 
 Experimental: false
 
 Orchestrator: swarm
 



[vagrant@localhost ~]$ docker --version


Docker version 18.05.0-ce, build f150324









5-CONFIGURE NON ROOT USER TO RUN DOCKER COMMANDS WITHOUT SUDO.

[vagrant@localhost ~]$ sudo usermod -aG docker vagrant



[vagrant@localhost ~]$ sudo su - vagrant

Last login: Tue Jul 17 18:39:42 +08 2018 from 10.0.2.2 on pts/0





[vagrant@localhost ~]$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE










6-TYPE DOCKER ON COMMANDLINE AND READ OUTPUT I.E CONTAINING RELATED COMMANDS.


[vagrant@localhost ~]$ docker

Usage:	docker COMMAND

A self-sufficient runtime for containers

Options:

      --config string      Location of client config files (default "/home/vagrant/.docker")
      
  -D, --debug              Enable debug mode
  
  -H, --host list          Daemon socket(s) to connect to
  
  -l, --log-level string   Set the logging level ("debug"|"info"|"warn"|"error"|"fatal") (default "info")
  
      --tls                Use TLS; implied by --tlsverify
      
      --tlscacert string   Trust certs signed only by this CA (default "/home/vagrant/.docker/ca.pem")
      
      --tlscert string     Path to TLS certificate file (default "/home/vagrant/.docker/cert.pem")
      
      --tlskey string      Path to TLS key file (default "/home/vagrant/.docker/key.pem")
      
      --tlsverify          Use TLS and verify the remote
      
  -v, --version            Print version information and quit
  

Management Commands:

  config      Manage Docker configs
  
  container   Manage containers
  
  image       Manage images
  
  network     Manage networks
  
  node        Manage Swarm nodes
  
  plugin      Manage plugins
  
  
  secret      Manage Docker secrets
  
  service     Manage services
  
  swarm       Manage Swarm
  
  system      Manage Docker
  
  trust       Manage trust on Docker images
  
  volume      Manage volumes

Commands:


  attach      Attach local standard input, output, and error streams to a running container
  
  build       Build an image from a Dockerfile
  
  commit      Create a new image from a container's changes
  
  cp          Copy files/folders between a container and the local filesystem
  
  create      Create a new container
  
  diff        Inspect changes to files or directories on a container's filesystem
  
  events      Get real time events from the server
  
  exec        Run a command in a running container
  
  export      Export a container's filesystem as a tar archive
  
  history     Show the history of an image
  
  images      List images
  
  import      Import the contents from a tarball to create a filesystem image
  
  info        Display system-wide information
  
  inspect     Return low-level information on Docker objects
  
  kill        Kill one or more running containers
  
  load        Load an image from a tar archive or STDIN
  
  login       Log in to a Docker registry
  
  logout      Log out from a Docker registry
  
  logs        Fetch the logs of a container
  
  pause       Pause all processes within one or more containers
  
  port        List port mappings or a specific mapping for the container
  
  ps          List containers
  
  pull        Pull an image or a repository from a registry
  
  push        Push an image or a repository to a registry
  
  rename      Rename a container
  
  restart     Restart one or more containers
  
  rm          Remove one or more containers
  
  rmi         Remove one or more images
  
  run         Run a command in a new container
  
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  
  search      Search the Docker Hub for images
  
  start       Start one or more stopped containers
  
  stats       Display a live stream of container(s) resource usage statistics
  
  stop        Stop one or more running containers
  
  
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  
  top         Display the running processes of a container
  
  unpause     Unpause all processes within one or more containers
  
  update      Update configuration of one or more containers
  
  version     Show the Docker version information
  
  wait        Block until one or more containers stop, then print their exit codes
  
  












7-DISPLAY SYSTEM INFORMATION USING DOCKER.


[vagrant@localhost ~]$ docker info 

Containers: 0

 Running: 0
 
 Paused: 0
 
 Stopped: 0
 
Images: 0

Server Version: 18.05.0-ce

Storage Driver: overlay2

 Backing Filesystem: xfs
 
 Supports d_type: true
 
 Native Overlay Diff: true
 
Logging Driver: json-file

Cgroup Driver: cgroupfs

Plugins:

 Volume: local
 
 Network: bridge host macvlan null overlay
 
 Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
 
Swarm: inactive

Runtimes: runc

Default Runtime: runc

Init Binary: docker-init

containerd version: 773c489c9c1b21a6d78b5c538cd395416ec50f88

runc version: 4fc53a81fb7c994640722ac585fa9ca548971871

init version: 949e6fa

Security Options:

 seccomp
 
  Profile: default
  
Kernel Version: 3.10.0-862.2.3.el7.x86_64

Operating System: CentOS Linux 7 (Core)

OSType: linux

Architecture: x86_64

CPUs: 1

Total Memory: 487.7MiB

Name: localhost.localdomain

ID: A7CO:5TDW:QE4M:6Y3Q:BDKZ:IUBG:WVVS:Q2EN:ORDP:6LD2:JPWQ:B5EK

Docker Root Dir: /var/lib/docker


Debug Mode (server): false

Registry: https://index.docker.io/v1/

Labels:

Experimental: false


Insecure Registries:

 127.0.0.0/8
 
Live Restore Enabled: false










8-CHECK WHETHER YOU CAN ACCESS/DOWNLOAD IMAGES FROM DOCKERHUB OR NOT.


[vagrant@localhost ~]$ docker pull nginx

Using default tag: latest

latest: Pulling from library/nginx

be8881be8156: Pull complete

f2f27ed9664f: Pull complete 

54ff137eb1b2: Pull complete 

Digest: sha256:a461bb9fdeddb777053c0b50dbbe8a83d0f82f1c4b6de2b9c0445596fd7c0217

Status: Downloaded newer image for nginx:latest




