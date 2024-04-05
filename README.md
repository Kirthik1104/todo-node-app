# Created CI/CD pipeline for Nodejs web application, using docker, jenkins, AWS EC2 & webhooks

### In this project, we will learn about  DevOps and DevSecOps tools in one project:

### Tools Covered:
-  Linux
-  Git and GitHub
-  Docker
-  Docker-compose
-  Jenkins CI/CD using web hooks
#

## Pre-requisites to implement this project:

-  AWS EC2 instance (Ubuntu) with instance type t2.large or micro and root volume 29GB.

-  Jenkins installed <br>
    - Reference: <b><a href="https://www.jenkins.io/doc/book/installing/linux/#long-term-support-release"><u> Jenkins installation </a></u></b>

-  Docker installled
```bash
    sudo apt-get update
    sudo apt-get install docker.io
```

#
## Steps for Jenkins CI/CD:
1)  Access Jenkins UI and setup Jenkins
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_1.png)

2) Enabled handshake between jenkins and github and generating ssh key-gen
   - Associating private key with jenkins
   - Associaating public key with github

   **Note when you build the application in jenkins, it pulls your repo and and creates a dumps in jenkins. Check below image**
   ![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_7.png)

   Add jenkins as a user inside docker group to allow jenkins to interact, build and run docker containers.
   ```bash
     sudo -a -G docker jenkins
   ```
   
#
## Ways to run your application:

1) Using docker
```bash
 sudo docker build . -t <image-name>
 sudo docker run -d -p 8000:8000 <image-name (same as above)>
```
Note you can access the application using host ip:host port

2) Using build steps in jenkins
```bash
run the above commands as build steps, so that you can run the application directly from jenkins build and not having to run the docker build and run manually. Check the below image
```
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_4.png)

3) Finally!! --> **Automate the CI/CD pipeline** and deploy the web application using webhooks, **orchestrating docker build and run using commit trigger in jenkins**. Check the below imaage for integration
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_5.png)
Adding the jenkins-url followed by /github-webhook/
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_3.png)
Enabling build trigger which will then trigger build steps on code commit to start the automatic CI/CD pipeline.

-Now make update to the js file and commit the changes and see the magic happen!
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_8.png)
![alt text](https://github.com/Kirthik1104/todo-node-app/blob/main/images/new_image_9.png)

nodejs todo application
