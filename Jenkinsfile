pipeline {
    agent any
    stages {
    
        stage('--Mvn clean package--') {
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
            	sh "ssh -T -i /home/jenkins/back-end-RDS.pem jenkins@3.11.97.214"
            }
        }
        
    }
}