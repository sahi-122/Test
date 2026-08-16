pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code is available in Jenkins'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                bat 'docker build -t jenkins-demo .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting application...'
                bat '''
                    docker stop jenkins-demo 2>nul
                    docker rm jenkins-demo 2>nul
                    docker run -d --name jenkins-demo -p 8082:80 jenkins-demo
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}