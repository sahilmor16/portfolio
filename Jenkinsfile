pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/<your-repo>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("portfolio-website")
                }
            }
        }

        stage('Stop Previous Container') {
            steps {
                script {
                    // Stop and remove old container if running
                    sh 'docker stop portfolio-website || true'
                    sh 'docker rm portfolio-website || true'
                }
            }
        }

        stage('Run New Container') {
            steps {
                script {
                    // Run latest container
                    sh 'docker run -d -p 80:80 --name portfolio-website portfolio-website'
                }
            }
        }
    }
}
