# Bipolar_Assignment
# Objective

This is a simple CI/CD project which is done using Jenkins, In this project we will deploy a simple hello world webapp using jenkins and monitor using prometheus and grafana

# Tools Used

1. Github
2. Jenkins
3. Docker
4. Dockerhub
5. Kubernetes
6. Prometheus
7. Grafana
8. Maven 

# Configuring all the tools

1. Installing Jenkins and maven
   
   Jenkins Server Details

      Operating System     : Ubuntu
   
      Hostname             : jenkins-ansible
   
      RAM                  : 2 GB
   
      CPU                  : 1 Core
   
      EC2 Instance         : t2.small

 3. Install Java
    
    java -version
    apt-get install openjdk-11-jdk 
    java -version

 4. Install Jenkins

     curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null

    echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null

    sudo apt-get update
    sudo apt-get install jenkins=2.361.3 -y

5. INSTALL MAVEN

   cd /opt/
   ls
   wget https://dlcdn.apache.org/maven/maven-3/3.9.1/binaries/apache-maven-3.9.1-bin.zip
   apt-get install unzip -y
   unzip apache-maven-3.9.1-bin.zip
   ls
   rm -rf apache-maven-3.9.1-bin.zip
   ls

6. CONFIGURE MANVEN HOME PATH
   
   vim ~/.bashrc
   export M2_HOME=/opt/apache-maven-3.9.1
   export PATH=$PATH:$M2_HOME/bin
   source ~/.bashrc

 BUILDING CI/CD PIPELINE
   1. In the first of jenkins pipeline we will take the code from the main repository 
    
   2. After taking out the code from the repository we will perform the test on code which we will be again taken from the main repository
    
   3. After the code is successfully tested we will build the project using maven 
    
   4. After successfully building maven project then we will dockerize the container
    
   5. After the we will Deploy the container in dockerhub
  
   6. And in the last step we will deploy the container in the kubernetes.
    
   
