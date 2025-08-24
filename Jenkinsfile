pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/sahilmor16/portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('portfolio-website')
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 80:80 portfolio-website'
            }
        }
    }
}
