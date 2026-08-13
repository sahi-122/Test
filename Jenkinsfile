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
                    docker stop jenkins-demo || exit /b 0
                    docker rm jenkins-demo || exit /b 0
                    docker run -d --name jenkins-demo -p 8081:80 jenkins-demo
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