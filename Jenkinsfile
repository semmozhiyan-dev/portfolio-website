pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t portfolio-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop portfolio-app || true
                docker rm portfolio-app || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name portfolio-app \
                -p 8090:80 \
                portfolio-app
                '''
            }
        }
    }
}
