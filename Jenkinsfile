pipeline {
    agent any

    environment {
        IMAGE_NAME = "hanuman-java-app"
        DOCKERHUB_USER = "saidharshan706"
        CONTAINER_NAME = "hanuman-container"
        CREDENTIALS_ID = "dockerhub-creds"
        PORT = "8080"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git credentialsId: 'github-creds', url: 'https://github.com/SAIDHARSHAN75/github-demo.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    d
