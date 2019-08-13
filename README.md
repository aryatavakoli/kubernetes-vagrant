# kubernetes-vagrant
Automatically deploys a local Virtual Kubernetes Cluster on a local machine. 
* Helpful for testing cluster enviroments.
* Every VM in the cluster only has Docker and/or Kubernetes Installed.
* Ansible Scripts in ```scripts/``` can be easily modified to install any additional software
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
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
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
$ sudo sh -c 'echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list'
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
## Running the Virtual Cluster
### Clone the Repo
```sh
$ git clone https://github.com/aryatavakoli/kubernetes-vagrant.git
```
### Change directory to cloned folder
```sh
$ cd kubernetes-vagrant
```
### Create and run the cluster
Running
```sh
$ vagrant up
```
will automatically:
1. Use Vagrant to create and network the required VMs.
2. Use Ansible to install and Configure Docker and Kubernetes

To stop the cluster:
```sh
$ vagrant halt
```
To delete the cluster and start fresh:
```sh
vagrant -f destroy
```
