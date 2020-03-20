# Ansible Installation

Ansible is an open-source automation platform. It is simple to set up and yet powerful. Ansible helps with configuration management, application deployment, and task automation.

### Pre-requisites

1. An AWS EC2 instance (on Control node)

### Installation steps:

#### on Amazon EC2 instance

1. Install python and python-pip
   ```sh
   yum install python
   yum install python-pip
   ```
1. Install ansible using pip check for version

   ```sh
   pip install ansible
   ansible --version
   ```

1. Create user called ansadmin (on Control node and Managed host)
   ```sh
   useradd ansadmin
   passwd ansadmin
   ```
1. Grant sudo access to ansadmin user.

   ```sh
   echo "ansadmin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
   ```

1. Log in as a ansadmin user on master and generate ssh key (on Control node)
   ```sh
   ssh-keygen
   ```
1. Copy keys onto all ansible managed hosts (on Control node)

   ```sh
   ssh-copy-id ansadmin@<target-server>
   ```

1. The Ansible server is used to create images and store on docker registry. Therfore install docker, start docker services and add ansadmin to the docker group.

   ```sh
   yum install docker

   # start docker services
   service docker start
   service docker start

   # add user to docker group
   usermod -aG docker ansadmin

   ```

1. Create a directory /etc/ansible and add an inventory file called "hosts". Add control node and managed hosts IP addresses to it.

### Validation test

1. Run ansible command as ansadmin user it should be successful (Master)
   ```sh
   ansible all -m ping
   ```
