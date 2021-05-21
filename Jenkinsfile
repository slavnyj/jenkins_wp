pipeline {
    agent { node { label 'production' } }

    stages {
        stage('Start MySQL') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if [ $( docker ps -a | grep mariadb | wc -l ) -gt 0 ]; then
                        echo "Container with DB exist, start container mariadb ..." && docker start mariadb
                    else
                        echo "Container does not exist. Create container with DB, name: mariadb ..." && docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name mariadb -v "$PWD/database":/var/lib/mysql -d mariadb:latest
                    fi
                    '''
            }
        }
        
        stage('Start Wordpress') {
            steps {
                sh label: '',
                    script: '''#!/bin/bash
                    if [ $( docker ps -a | grep wordpress | wc -l ) -gt 0 ]; then
                        echo "Container with Wordpress exist, start container wordpress ..." && docker start wordpress
                    else
                        echo "Container does not exist. Create container with Wordpress, name: wordpress ..." && docker run -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=rootpass --name wordpress --link mariadb:mysql -p 80:80 -v "$PWD/html":/var/www/html -d wordpress
                    fi
                    '''
            }
        }
    }
}