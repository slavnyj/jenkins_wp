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
                        cd ~/wordpress && touch yes
                    else
                        cd ~/wordpress && touch not
                    fi
            '''
            }
        }
    }
}