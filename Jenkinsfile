
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t sara-docker-app:latest .'
                echo 'Docker image built successfully!'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker rm -f sara-docker-container || exit 0'
                bat 'docker run -d --name sara-docker-container -p 8081:80 sara-docker-app:latest'
            }
        }
    }
}
