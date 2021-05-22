pipeline {
    agent any

    stages {
        stage('Production uptime') {
            steps {
                node ('productiom') {
                    sh 'uptime -p'
                }
            }
        }
        
        stage('Staging uptime') {
            steps {
                node ('staging') {
                    sh 'uptime -p'
                }
            }
        }
    }
}