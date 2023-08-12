# DevOps-Project-2
- In this project, I build and deploy my application on Docker Container with the help of Ansible.
![Commit Code](https://github.com/rutikdevops/DevOps-Project-2/assets/109506158/2a2802e7-8dad-4d7a-ab47-9043f1aee546)
# Project Blog link :-
# Project Steps :-
- Create 4 ec2 instance name as:- (AWS Linux-2, t2 micro)
1. Jenkins-Server
2. Ansible-Server
3. Docker-Server
4. Tomcat-Server

# 1. Install  and Configure the Jenkins :-
```bash
ec2-user
sudo su
yum update -y
hostnamectl set-hostname jenkins
bash
```
- Java installation on Jenkins server:-
```bash
yum install java* -y
java --version
alternatives --config java               ## Using this command you can choose any version of Java
```

- Jenkins installation on Jenkins server:-
```bash
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
yum install jenkins -y
systemctl enable jenkins.service
systemctl start jenkins.service
systemctl status jenkins.service
```
- Copy public ip of jenkins server and paste it in new tab with port no.8080
<img width="576" alt="image" src="https://github.com/rutikdevops/DevOps-Project-2/assets/109506158/75d4392c-c663-441e-baa8-39c11af26ead">

- copy this path and paste in terminal with "cat" command
```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```
- Now copy & paste this passwd in jenkins. so, jenkins is ready.



# 2. Install and Configure the Maven :-
```bash
sudo su
cd ~
pwd
cd /opt
wget https://dlcdn.apache.org/maven/maven-3/3.9.4/binaries/apache-maven-3.9.4-bin.tar.gz
tar -xvzf apache-maven-3.9.4-bin.tar.gz
mv apache-maven-3.9.4 maven
cd maven/
cd bin/
./mvn -v
```
```bash
cd ~
ll -a
vim .bash_profile
```
- In the vi editor add this path :-
<img width="373" alt="image" src="https://github.com/rutikdevops/DevOps-Project-2/assets/109506158/9db87c99-c213-4f9a-bec4-9f92591ea521">
```bash
M2_HOME=/opt/maven
M2=/opt/maven/bin
JAVA_HOME=/usr/lib/jvm/java-11-amazon-corretto.x86_64
PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2
 ```
- Find java path using this command:-
```bash
find / -name java-11*
```
- Showing maven & java path :-
```bash
source .bash_profile
echo $PATH
```



# 3. Install Maven Plugin and cinfigure Jenkins for Maven :-









