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
                // Your build steps here
                // Example: docker build -t "alpine:latest" .
                bat 'docker build -t "alpine:latest" .'
            }
        }
        stage('Push Docker Image') {
            steps {
                // Login to Docker Hub
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerCredentialsId') {
                        bat 'docker login -u d32saurav339 -p Saurav@389421'
                    }
                }
                // Tag the Docker image
                script {
                    docker.tag('alpine:latest', 'd32saurav339/library:alpine')
                }
                // Push the Docker image
                script {
                    docker.image('d32saurav339/library:alpine').push()
                }
            }
        }
    }
}
