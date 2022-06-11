#!groovy
pipeline {
    agent any
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build Image') { 
            steps { 
                script{
                 app = docker.build("weblight")
                }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'ecr:ap-south-1:b77403f9-9a7d-4965-9c19-8fee61797a09', url: '585300280710.dkr.ecr.ap-south-1.amazonaws.com/frontend_app') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }
    }
}
