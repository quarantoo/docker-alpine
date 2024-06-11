pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                // Your build steps here
                // Example: docker build -t "alpine:latest" .
                bat 'docker build -t "alpine:latest" .'
            }
        }
        stage('Push Docker Image') {
            steps {
                // Login to Docker Hub
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'ff1a2c83-1f74-45dd-b49b-afc68d7d460a') {
                        bat 'docker login -u d32saurav339 -p Saurav@389421'
                    }
                }
                // Tag and push the Docker image
                script {
                    docker.image('alpine:latest').push('d32saurav339/library:alpine')
                }
            }
        }
    }
}

