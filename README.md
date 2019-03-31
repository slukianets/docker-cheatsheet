Docker Cheatsheet
===
Table of content
---
[1.Install](#centos-75-installation)
Install
---

### CentOS 7.5 installation
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
### Ubuntu 18.04 installation
[link](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
##### install
```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get-update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
##### verify
```
sudo systemctl status docker
sudo docker info
sudo docker run hello-world
```
