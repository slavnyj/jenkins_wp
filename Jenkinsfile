pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Start MySQL') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if if [ $( docker ps -a | grep dbwordpress | wc -l ) -gt 0 ]; then
                        cd ~/wordpress && touch 11111
                    else
                        cd ~/wordpress && touch 22222
                    fi
            '''
            }
        }
    }
}