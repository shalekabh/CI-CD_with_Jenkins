# Creating a Jenkins server

### Set up an Ec2 instance

Set up an instance with the correct name, with the correct AMI, I used ubuntu 20.04. 

Set up SG groups to allow SSH, HTTP and 3000. 

Set up user data to run nginx:

Run instance:

SSH to instance and install the following dependencies:

Install OpenJDK 11 (Java Development Kit) - ```sudo apt install openjdk-11-jdk```

```java -version```
```sudo apt install git ```
```sudo apt install curl```
```sudo apt install unzip```

This installs git, curl and unzip.

```sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA``` - this gets the correct gpg key (make sure its correct for the ami youre using)

```sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'```  - So, the overall purpose of the command is to add the Jenkins package repository URL (deb http://pkg.jenkins.io/debian-stable binary/) to the jenkins.list file within the /etc/apt/sources.list.d/ directory. This allows the package manager (apt) to access the Jenkins packages and install them on the system.

```sudo apt update```

```curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -```
```sudo apt-get install -y nodejs``` - these install node.js

```sudo apt install jenkins```

```sudo systemctl start jenkins```
```sudo systemctl enable jenkins```
```sudo systemctl status jenkins```
```q```

Jenkins should now be installed and running on your Ubuntu 20.04 AWS instance. Access the Jenkins web interface by opening your browser and navigating to http://<your-instance-IP>:8080. Follow the on-screen instructions to complete the Jenkins setup.

### Jenkins on screen setup

The webpage will ask you to get a password from a directory and copy it into the page, to read the passowrd use this command:

``` sudo cat /var/lib/jenkins/secrets/initialAdminPassword```

copy it into the webpage for jenkins and proceed:

Next choose and load plugins,  used reccommended:

![Alt text](pic_for_mds-jenkins/customize%20jenkins.png)
![Alt text](pic_for_mds-jenkins/loading%20plugins%20jenkins.png)

Next create an admin user:

![Alt text](pic_for_mds-jenkins/create%20admin%20user.png)

Then Jenkins is nearly ready click Start using Jenkins and it will take you to the home page:

![Alt text](pic_for_mds-jenkins/jenkins%20is%20ready.png)
![Alt text](pic_for_mds-jenkins/jenkins%20home.png)