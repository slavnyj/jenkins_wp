pipeline {
    agent { node { label 'master' } }
    triggers {
        cron('H/5 * * * *')
    }
    stages {
        stage('Ping production') {
            steps {
                sh 'ping -c 10 84.252.141.170'
            }
        }
        
        stage('Ping staging') {
            steps {
                sh 'ping -c 10 84.252.140.249'
            }
        }
    }
}