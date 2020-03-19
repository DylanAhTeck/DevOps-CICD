# DevOps-CICD

Given an existing Java project, I was responsible for setting up a CD/CI pipeline. 



### Jenkins with AWS

Jenkins is a self-contained Java-based program, ready to run out-of-the-box, with packages for Windows, Mac OS X and other Unix-like operating systems. As an extensible automation server, Jenkins can be used as a simple CI server or turned into the continuous delivery hub for any project.

Steps:
1) Created an EC2 instance
2) Installing Java v1.8x on the Linux machine
3) Installing and configuring Jenkins using the repository


Get the latest version of jenkins from https://pkg.jenkins.io/redhat-stable/ and install
```bash
yum -y install wget
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum -y install jenkins
```
####Start Jenkins
```bash
# Start jenkins service
service jenkins start

# Setup Jenkins to start at boot,
chkconfig jenkins on
```
####Accessing Jenkins
By default jenkins runs at port 8080:
```bash
http://YOUR-SERVER-PUBLIC-IP:8080
```
