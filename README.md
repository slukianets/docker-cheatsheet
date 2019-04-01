Docker Cheatsheet
===
Table of content
---
1. [Install](#1-install)
2. [First Containers](#2-first-containers)

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
