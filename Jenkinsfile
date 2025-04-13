pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/OmDidolkar564/my-app.git'
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
                    sh 'docker rm -f my-app || true'
                    sh 'docker run -d -p 3000:3000 --name my-app my-app-image'
                }
            }
        }
    }
}
