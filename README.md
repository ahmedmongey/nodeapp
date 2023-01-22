# nodeapp applicition 
______________________
this repo for deploying a nodeapp website using CICD pipeline using 
- Docker 
- AWS cloud provider
- jenkins 
- GitHub

#pre-requstes :
  - AWS account
  - DockerHub account
  - Jenkins installed
  - Github repo
  
#how to run 
______________
  step one 
    is installing jenkins and important plugins for pipeline process , you can run it by
      Public IPv4 address : 8080
  step two 
    is typing your jenkinsfile by its stages which you need for running your website 
      stage one is Cloning your Github repo
      stage two is Building your image by Dockerfile 
      stage three is Deploy your image
  
  step three 
    is building your job on jenkins
  
  step four
    is pushing the image to your instance and run it 
      docker run -it -p 3000:3000 <imagename>:<tag>
      
  step five 
    is going to browser and run
  
 
      Public IPv4 address:3000
      Public IPv4 address:3000/will
      Public IPv4 address:3000/ready 
