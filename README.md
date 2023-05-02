Sonar-scanner deployment script that you can use to install sonar-scanner on Vagrant VM and point it to your sonarqube server to scan your code for vulnerabilities.
You can find sonarqube server deployment script [here.](https://github.com/stoykovstoyk/sonarqube-ansible-deployment)

# Requirements #

* Vagrant 
* VirtualBox 

## How to use this repo on Ubuntu 22.04 ##

### Install Vagrant ###
```shell
$ sudo apt update -y
$ sudo apt install vagrant -y
```
### Install Vagrant SCP plugin ###
```shell
$ vagrant plugin install vagrant-scp
```
### Install VirtualBox ###
``` shell
$ sudo apt install virtualbox -y
```
### Clone this repo & create Vagrant VM ###
```shell
$ git clone https://github.com/stoykovstoyk/sonar-scanner-ansible-deployment.git
$ cd sonar-scanner-ansible-deployment
$ vagrant up
```
### 

### Copy your project source code to sonar-scanner VM ###
```shell
vagrant scp src/ /vagrant
```

### Login to Vagrant VM where your project source code is ###
```shell
$ vagrant ssh -- -t 'cd /vagrant/src && bash'
```
### Run sonar-scanner with params provided by sonarqube server ###
Example:
```shell
$ sonar-scanner \n
   -Dsonar.projectKey=example \n
   -Dsonar.sources=. \n
   -Dsonar.host.url=http://sonarqube.localhost:8080 \n
   -Dsonar.token=sqp_bcc9999999999999999999999999999
```
Finally, open sonarqube server URL and check results.

In this example sonarqube server is located at http://sonarqube.localhost:8080 
