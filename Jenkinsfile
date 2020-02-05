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
            sh 'docker build -t alwinthomas/app-frontend .'
          }
        }
        stage('--docker-publish--') {
          steps {
              withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {
              sh 'docker push alwinthomas/app-frontend:latest'
              }
          }
        }
    }
}