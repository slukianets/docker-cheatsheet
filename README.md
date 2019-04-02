Docker Cheatsheet
===
Table of content
---
1. [Install](#1-install)
2. [First Containers](#2-first-containers)
3. [container commands](#3-container-commands)
4. [images commands](#4-images-commands)

## 1. Install

### 1.1 CentOS 7.x installation
[link](https://docs.docker.com/install/linux/docker-ce/centos/)
##### install
```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
sudo systemctl enable docker
sudo systemctl start docker
```
##### verify
```
sudo systemctl status docker
sudo docker info
sudo docker run hello-world
```
### 1.2 CentOS 7.6 with Vagrant/Virtualbox
```
cd centos-configured
vagrant up
vagrant ssh
```
### 1.3 Ubuntu 18.04 installation
[link](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
##### install
```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
##### verify
```
sudo systemctl status docker
sudo docker info
sudo docker run hello-world
```
## 2. First Containers
##### hello-world
```
docker run hello-world
```
##### centos
```
docker run -it centos
cat /etc/centos-release
du -sh / 2>/dev/null
```
##### ubuntu
```
docker run -it ubuntu
cat /etc/debian_version
cat /etc/issue
du -sh / 2>/dev/null
```
##### alpine
```
docker run -it alpine
cat /etc/alpine-release
cat /etc/issue
du -sh / 2>/dev/null
```
##### busybox
```
docker run -it busybox
du -sh /
```
## 3. Containers commands
### 3.1 List
```
# show running containers
docker ps
# show last container
docker ps -l
# show all containers ( including stopped )
docker ps -a
# show container sizes
docker ps -s
```
##### full container ID
```
[root@desktop-08ut1lq ~]# docker ps -lq --no-trunc
cb9defb0841671a779f1527e5e30aa6c8b03d9bad9a42e61875368a9de6ae5f7
[root@desktop-08ut1lq ~]# docker ps -l
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
cb9defb08416        busybox             "sh"                11 minutes ago      Exited (0) 11 minutes ago                       gracious_villani
```
### 3.2 Run
```
# run in interactive mode
docker run -it ubuntu
# run in background
docker run -d httpd
# detach: Ctrl^P, Ctrl^Q
# attach <cid>
docker attach fe8
# run interactive in background
docker run -itd ubuntu
# check running
docker ps
```
### 3.3 Stop
```
# try gracefully stop container (SIGTERM, 10s wait)
docker stop <cid>
# just kill
docker kill <cid>
```
### 3.4 Read Logs
```
# show logs
docker logs <cid>
# show last 5 lines
docker logs --tail 5 <cid>
# tail -f
docker logs --tail 5 --follow <cid>
```
##### httpd example
```
docker run -d -P httpd
docker port $(docker ps -lq)
-> 80/tcp -> 0.0.0.0:32768
# on another console generate load
while sleep 1; do curl localhost:32768; done
# on main console
docker logs --tail 1 --follow $(docker ps -lq)
```
### 3.5 Exec
```
# exec something in running container
docker exec -it <cid> '/bin/bash'
```
## 4. Images commands
```
# list
docker images
# download
docker pull
# delete
docker rm
```
## 5. Dockerfile
### 5.1 nslookup
##### v1
```
# create environment
cd /vagrant
touch Dockerfile
# edit ...
cat Dockerfile
FROM centos
RUN yum install -y bind-utils
# docker build -t tag, nslookup - image name
docker build -t nslookup .
```
##### v2
```
FROM centos
RUN yum install -y bind-utils
ENTRYPOINT ["nslookup"]
CMD ["google.com"]
```
