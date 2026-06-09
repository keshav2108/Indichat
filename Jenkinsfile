
pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USERNAME/messaging-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t messaging-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop messaging-app || true
                docker rm messaging-app || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d                         --name messaging-app                         -p 3000:3000                         messaging-app
                '''
            }
        }
    }
}
