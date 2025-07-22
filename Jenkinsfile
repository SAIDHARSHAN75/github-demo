pipeline {
    agent {
        label 'slave'
    }

    stages {
        stage('Check OS Version') {
            steps {
                sh 'cat /etc/os-release'
            }
        }

        stage('List Running Services') {
            steps {
                sh 'systemctl list-units --type=service --state=running'
            }
        }

        stage('Show Network Interfaces') {
            steps {
                sh 'ip addr show'
            }
        }

        stage('Check Open Ports') {
            steps {
                sh 'ss -tuln'
            }
        }

        stage('Uptime') {
            steps {
                sh 'uptime'
            }
        }
    }
}

