# CICD-GiT-Maven-Jenkins-Docker
1. Launch an EC2 instance for the Docker host
2. Install docker on EC2 instance and start services `yum install docker` `service docker start`
3. Create a new user for Docker management and add him to the Docker (default) group
      `useradd dockeradmin
       passwd dockeradmin
       usermod -aG docker dockeradmin`
5. Write a Docker file under /opt/docker
6. Login to Jenkins console and add Docker server to execute commands from Jenkins  
          `Manage Jenkins --> Configure system -->  Publish over SSH --> add Docker server and credentials`
7. Create Jenkins job 
A) Source Code Management  
 Repository : https://github.com/Nikunz/CICD-GiT-Maven-Jenkins-Docker.git
 Branches to build : */main  
B) Dokcer Ecec commands:
          `docker stop docker_demo;
          docker rm -f docker_demo;
          docker image rm -f docker_demo;
          cd /opt/docker;
          docker build -t docker_demo.`
C) send files or execute commands over SSH  
  Name: `docker_host`  
  Exec command: `docker run -d --name docker_demo -p 8090:8080 docker_demo`  

7. Login to the Docker host and check images and containers. (no images and containers)

8. Execute Jenkins job

9. Check images and containers again on the Docker host on AWS EC2. This time an image and container get created through Jenkins job

10. Access web application from the browser which is running on the container
```
<docker_host_Public_IP>:8090
```
