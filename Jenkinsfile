pipeline {
    agent any

    environment {
        IMAGE_NAME = "hanuman-java-app"
        DOCKERHUB_USER = "saidharshan706"
        CONTAINER_NAME = "hanuman-java"
        CREDENTIALS_ID = "dockerhub-creds"
        PORT = "8080"
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-creds', url: 'https://github.com/SAIDHARSHAN75/java-hanuman-app.git'
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
                    dockerImage = docker.build("${DOCKERHUB_USER}/${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${CREDENTIALS]()
