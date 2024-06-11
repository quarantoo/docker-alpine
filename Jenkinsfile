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
                    sh 'docker login -u d32saurav339 -p Saurav@389421' {
                        def dockerImage = docker.image('alpine:latest')
                        dockerImage.tag('latest')
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
