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
                bat 'docker build -t d32saurav339/alpine:latest .'
            }
        }
        stage('Push Docker Image') {
            steps {
                // Login to Docker Hub
                script {
                        bat 'docker login -u d32saurav339 -p Saurav@389421'
                        bat 'docker push d32saurav339/alpine:latest
                    }
                }
            }
        }
    }
