pipeline {
    agent any

    stages {

        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/Harini0712/chess-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t static-site .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop static-site || true'
                sh 'docker rm static-site || true'
                sh 'docker run -d -p 8081:8081 --name static-site static-site'
            }
        }
    }
}
