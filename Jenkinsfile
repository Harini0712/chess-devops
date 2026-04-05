pipeline {
    agent any

    stages {
        stage('Clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Harini0712/chess-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-site .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop static-site || true'
                sh 'docker rm static-site || true'
                sh 'docker run -d -p 80:80 --name static-site static-site'
            }
        }
    }
}