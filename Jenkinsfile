pipeline {
    agent any
    
    stages {
        stage('Print Hostname')
                steps{
                sh 'Hostname'
            }
        }
        stage('Ip Address'){
        steps{
            sh'hostname -I'
        }     
    }
stage ('Cpu Details'){
    steps{
sh 'lscpu'
    }
}
stage('Disk uage'){
    steps{
        sh 'df -kh'
    }
}
    stage('Memory usage'){
        steps{
            sh 'free -h'
        }
    }
}
}
