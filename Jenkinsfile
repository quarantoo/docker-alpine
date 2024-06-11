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
                    // Build Docker image
                    def dockerImage = docker.build('alpine:latest')
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'ff1a2c83-1f74-45dd-b49b-afc68d7d460a') {
                        def dockerImage = docker.image('alpine:latest')
                        dockerImage.tag('latest')
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
