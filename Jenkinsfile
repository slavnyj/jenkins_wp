pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Test') {
            steps {
                sh(returnStdout: true, script: '''#!/bin/bash
                    if docker ps -q -f name=wordpressdb;
                    then
                        echo "Found file"
                    else
                        echo "Did not find file"
                    fi
            '''.stripIndent())
            }
        }
    }
}