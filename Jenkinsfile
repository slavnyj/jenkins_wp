pipeline {
    agent any

    stages {
        stage('Start MySQL') {
            steps {
                echo 'Start MariaDB'
                sh '''
                    mkdir ~/wordpress && cd ~/wordpress
                    docker pull wordpress
                    docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name wordpressdb -v "$PWD/database":/var/lib/mysql -d mariadb:latest'''
            }
        }
        stage('Start Wordpress') {
            steps {
                echo 'Start Wordpress'
                sh '''
                    cd ~/wordpress
                docker pull wordpress
                docker run -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=rootpass --name wordpress --link wordpressdb:mysql -p 80:80 -v "$PWD/html":/var/www/html -d wordpress'''
            }
        }
    }
}



