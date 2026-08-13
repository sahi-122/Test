pipeline {
    agent any

    stages {

        stage('Test Docker') {
            steps {
                bat 'whoami'
                bat 'echo %PATH%'
                bat 'where docker'
                bat 'docker --version'
                bat 'docker version'
            }
        }
    }
}