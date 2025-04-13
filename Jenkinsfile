pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/OmDidolkar564/my-app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-app-image')
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker rm -f my-app || true'
                    bat 'docker run -d -p 3000:3000 --name my-app my-app-image'
                }
            }
        }
    }
}
