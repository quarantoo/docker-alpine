pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/quarantoo/docker-alpine.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('alpine:latest')
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://hub.docker.com', 'ff1a2c83-1f74-45dd-b49b-afc68d7d460a') {
                        docker.image('alpine:latest').push('latest')
                    }
                }
            }
        }
    }
}
