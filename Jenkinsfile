pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t continuousdeployment .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop continuousdeployment || exit 0'
                bat 'docker rm continuousdeployment || exit 0'
                bat 'docker run -d -p 5400:5000 --name continuousdeployment'
            }
        }
    }
}
