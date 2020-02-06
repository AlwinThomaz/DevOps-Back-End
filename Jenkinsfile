pipeline {
    agent any
    stages {
    
        stage('--Mvn clean package deploy--') {
                steps {
                    sh "mvn clean package deploy"
                    }
            }
            stage('--docker-build--') {
          steps {
            sh 'docker build -t alwinthomas/app-backend .'
          }
        }
        stage('--docker-publish--') {
          steps {
              withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {
              sh 'docker push alwinthomas/app-backend:latest'
              }
          }
        }
          
        stage('--ssh--') {
            steps {
            	sh "ssh -T -i /home/jenkins/back-end-RDS.pem ubuntu@ec2-3-8-173-215.eu-west-2.compute.amazonaws.com ./back-end-ssh.sh"
            }
        }
        
    }
}