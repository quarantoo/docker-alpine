pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
                git 'https://github.com/quarantoo/docker-alpine.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.build('alpine:3.14')
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                // Push the Docker image to a registry
                script {
                    docker.withRegistry('https://hub.docker.com', 'ff1a2c83-1f74-45dd-b49b-afc68d7d460a') {
                        docker.image('alpine:3.14').push('3.14')
                    }
                }
            }
        }
    }
}
