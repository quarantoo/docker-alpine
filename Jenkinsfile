pipeline {
    agent any

    stages {
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    bat 'docker build -t "alpine:latest" .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to the registry
                    docker.withRegistry('https://index.docker.io/v1/', 'ff1a2c83-1f74-45dd-b49b-afc68d7d460a') {
                        def dockerImage = docker.image('alpine:latest')
                        dockerImage.push()
                    }
                }
            }
        }
    }
}

