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
                sh 'docker build -t jenkins-demo .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting application...'

                sh '''
                    docker stop jenkins-demo || true
                    docker rm jenkins-demo || true
                    docker run -d --name jenkins-demo -p 8080:80 jenkins-demo
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