pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t portfolio-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop portfolio-app || true
                docker rm portfolio-app || true

                docker run -d \
                --name portfolio-app \
                -p 8090:80 \
                portfolio-app
                '''
            }
        }
    }
}
