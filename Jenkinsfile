pipeline {
    agent any
    //agent { node { label 'staging' } }

    stages {
        stage('Test') {
            steps {
                sh(returnStdout: true, script: '''#!/bin/bash
                    if [ docker container inspect wordpressdb ];then
                    echo "Found file"
                    else
                    echo "Did not find file"
                    fi
            '''.stripIndent())
            }
        }
    }
}
       /*stage('Start MySQL') {
            steps {
                echo 'Start MariaDB container'
                script {
                    def inspectExitCode = sh script: "docker ps -a --format '{{.Names}}' | grep wordpressdb", returnStatus: true
                    if (inspectExitCode == 0) {
                        sh "echo "Container exist 1" "
                    }else {
                        sh script: "echo "DOnt Container exist 0" "
                    }}
                /*sh(returnStdout: true, script:'''#!/bin/bash -xe
                    if docker ps -a --format '{{.Names}}' | grep wordpressdb;
                    then
                        echo "Container exist, start container"
                        docker start wordpressdb
                    else
                        echo "Container does not exist"
                        docker run -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=wordpress --name wordpressdb -v "$PWD/database":/var/lib/mysql -d mariadb:latest
                    fi
                '''.stripIndent())*/
                
    
        /*stage('Start Wordpress container') {
            steps {
                echo 'Start Wordpress'
                sh(returnStdout: true, script:'''#!/bin/bash -xe
                    #!/bin/bash
                    cd ~/wordpress
                    if docker ps -a --format '{{.Names}}' | grep wordpress;
                    then
                        echo "Container exist, start container"
                        docker start wordpress
                    else
                        echo "Container does not exist"
                        docker run -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=rootpass --name wordpress --link wordpressdb:mysql -p 80:80 -v "$PWD/html":/var/www/html -d wordpress
                    fi'''.stripIndent())
            }*/
        
    



