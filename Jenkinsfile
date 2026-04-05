pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    sh 'docker build -t chess-app .'
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop chess-container || true'
                sh 'docker rm chess-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 80:80 --name chess-container chess-app'
            }
        }
    }
}
