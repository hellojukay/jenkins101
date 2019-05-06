# Jenkins101
这是一个 jenkins 的中文介绍教程．

## 安装 Jenkins
* docker 安装
直接使用 docker run 安装最新版本的 jenkins
```shell
docker run -u root --rm -it -d -p 8080:8080  -p 50000:50000  -v jenkins-data:/var/jenkins_home  -v /var/run/docker.sock:/var/run/docker.sock  jenkinsci/blueocean 
```
当然，　也可以使用　docker-compose 来安装
```shell
docker-compose up -d
```
```yml
version: '3'
services:
    jenkins:
    image: 'jenkins/jenkins:lts'
    container_name: jenkins
    restart: always
    ports:
        - '8080:8080'
        - '50000:50000'
    volumes:
        jenkins_home:/var/jenkins_home
volumes:
    jenkins_home:
        external: true
```
* JAVA War 包安装
```shell
java -jar jenkins.war
```
* yum,apt,brew,pacman安装
通过包管理工具也能安装 jenkins

1. yum 安装 jenkinsfile
```shell
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum install jenkins
```
2. apt 安装 jenkins
```shell
wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```
3. mac 上 brew 安装 jenkins
```shell
brew update && brew install jenkins
```
4. arch 上使用 pacman　安装 jenkins
```shell
pacman -S jenkins
```