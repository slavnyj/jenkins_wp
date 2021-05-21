pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Start MySQL') {
            steps {
                echo 'Start MariaDB container'
                sh '''
                    #!/bin/bash
                    mkdir ~/wordpress && cd ~/wordpress
                    if [ "$$(docker ps -a | grep wordpressdb)" ]
                    then
                        echo "Container exist, start container"
                        docker start wordpressdb
                    else
                        echo "Container does not exist"
                        docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name wordpressdb -v "$PWD/database":/var/lib/mysql -d mariadb:latest
                    fi'''
            }
        }
        stage('Start Wordpress container') {
            steps {
                echo 'Start Wordpress'
                sh '''
                    #!/bin/bash
                    cd ~/wordpress
                    if [ "$$(docker ps -a | grep wordpress)" ]
                    then
                        echo "Container exist, start container"
                        docker start wordpress
                    else
                        echo "Container does not exist"
                        docker run -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=rootpass --name wordpress --link wordpressdb:mysql -p 80:80 -v "$PWD/html":/var/www/html -d wordpress
                    fi'''
            }
        }
    }
}



