pipeline {
    agent any
	
	  tools
    {
       maven "maven 3.9.0"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/abiola911/CI-CD-using-Docker.git'
             
          }
        }
	 stage("maven 3.9.0") {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp emjay123/samplewebapp:latest'
                //sh 'docker tag samplewebapp emjay123/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
          sh  'docker push emjay123/samplewebapp:latest'
        //  sh  'docker push emajy123/samplewebapp:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
                sh "docker run -d -p 8003:8080 emjay123/samplewebapp"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.84.102 run -d -p 8003:8080 emjay123/samplewebapp"
 
            }
        }
    }
	}
