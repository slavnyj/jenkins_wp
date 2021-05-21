pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Test') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if docker ps -q -f name=wordpressdb;
                    then
                        cd ~/wordpress && touch 11111
                    else
                        cd ~/wordpress && touch 22222
                    fi
            '''
            }
        }
    }
}