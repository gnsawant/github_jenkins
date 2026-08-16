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
                bat 'docker build -t tut5 .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop tut5 || exit 0'
                bat 'docker rm tut5 || exit 0'
                bat 'docker container run -d -p 5400:5000 --name tut5'
            }
        }
    }
}
