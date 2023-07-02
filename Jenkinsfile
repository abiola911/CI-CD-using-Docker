pipeline {
    agent any
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/abiola911/CI-CD-using-Docker.git'
             
          }
        }
  stage('Run Docker Container on Jenkins') {
           steps {
             
                sh 'docker run hello-world'             
          }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.84.102 run hello-world"
 
            }
        }
    }
}
