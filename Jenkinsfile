pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t booknest-app .'
            }
        }
        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f booknest || true'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8084:80 --name booknest booknest-app'
            }
        }
    }
}