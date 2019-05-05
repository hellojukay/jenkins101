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
* yum,apt,brew,pacman安装
