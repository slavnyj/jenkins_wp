pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Test') {
            steps {
                sh label: '',
                    script: ''' #!/bin/bash
                   ls
                   pwd
                   '''
            }
        }
    }
}