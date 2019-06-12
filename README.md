# kubernetes-vagrant
Creates a local Virtual Kubernetes Cluster using Vagrant and Ansible. Helpful for testing cluster enviroments.

## Dependencies 
* Ansible
* Python and pip
* Virtual Box
* Vagrant

## Installing Dependencies (Ubuntu)
### Install Python and Pip:
```sh
$ sudo apt update
$ sudo apt install python3 python3-pip #python3
$ sudo apt install python python-pip #python2
```
### Install Ansible
```sh
$ sudo pip install ansible:
```
### Install prerequisites
```sh
$ sudo apt update
$ sudo apt install gcc make linux-headers-$(uname -r) dkms
```
### Install Virtualbox
Add the repository keys
```sh
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - 
```
Add Virutalbox package repository
```sh
$ sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" >> /etc/apt/sources.list.d/virtualbox.list
```
Install Virutalbox
```sh
$ sudo apt update
$ sudo apt install virtualbox-6.0
```
### Install Vagrant
Get latest realease of Vagrant. Replace ${VER} with latest version of Vagrant (i.e 2.2.4)
```sh
$ wget https://releases.hashicorp.com/vagrant/${VER}/vagrant_${VER}_x86_64.deb
```
```sh
$ sudo dpkg -i vagrant_${VER}_x86_64.deb
```
