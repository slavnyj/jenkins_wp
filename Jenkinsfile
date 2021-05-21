pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Start MySQL') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if docker ps -q -f name=dbwordpress;
                    then
                        echo "Container exist" && docker start dbwordpress
                    else
                        echo "Container does not exist" && docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name dbwordpress -v "$PWD/database":/var/lib/mysql -d mariadb:latest
                    fi
            '''
            }
        }
    }
}