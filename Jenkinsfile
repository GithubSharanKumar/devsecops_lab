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
                bat 'docker build -t talkbox .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker rm -f talkbox || exit /b 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 9090:80 --name talkbox talkbox'
            }
        }
    }
}