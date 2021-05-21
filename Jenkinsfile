pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Start MySQL') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if [ $( docker ps -a | grep dbwordpress | wc -l ) -gt 0 ]; then
                        docker start dbwordpress
                    else
                        docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name dbwordpress -v "$PWD/database":/var/lib/mysql -d mariadb:latest
                    fi
                    '''
            }
        }
    }
}