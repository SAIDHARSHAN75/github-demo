pipeline {
    agent any

    environment {
        IMAGE_NAME = "hanuman-site"
        CONTAINER_NAME = "hanuman-container"
        DOCKERHUB_USER = "saidharshan706"   //
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/SAIDHARSHAN75/hanuman-ci-cd.git' //
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${DOCKERHUB_USER}/${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Docker Hub Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh "docker push ${DOCKERHUB_USER}/${IMAGE_NAME}:${BUILD_NUMBER}"
            }
        }

        stage('Deploy Container') {
            steps {
                sh "docker rm -f ${CONTAINER_NAME} || true"
                sh "docker run -d --name ${CONTAINER_NAME} -p ${PORT}:80 ${DOCKERHUB_USER}/${IMAGE_NAME}:${BUILD_NUMBER}"
            }
        }
    }

    post {
        success {
            echo "🚀 Jai Hanuman! Visit: http://<your-ip>:${PORT}"
        }
        failure {
            echo "❌ Something went wrong. Jai Bajrang Bali still blesses you!"
        }
    }
}
