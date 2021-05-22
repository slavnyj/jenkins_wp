pipeline {
    agent { node { label 'master' } }
    parameters {
        choice(
            choices: ['PRODUCTION', 'STAGING', 'BOTH'],
            description: 'Select the Environement from the Dropdown List',
            name: 'ENV')
    }

    stages {
        stage ('Reboot production') {
            when {
                expression { params.ENV == 'PRODUCTION' }
            }
            steps {
                node ('production') {
                    echo "Rebooting production server! ..."
                    sh 'sudo reboot'
                    retry(20){
                        sleep time: 5 unit: 'SECONDS'
                        sh 'ssh -o ConnectTimeout=1 84.252.141.170 exit'
}
                }
                
            }
        }

        stage ('Reboot staging') {
            when {
                expression { params.ENV == 'STAGING' }
            }
            steps {
                node ('staging') {
                    echo "Rebooting staging server! ..."
                    sh 'sudo reboot'
                }
                
            }
        }

        stage ('Reboot both envs') {
            when {
                expression { params.ENV == 'BOTH' }
            }
            steps {
                node ('production') {
                    echo "Rebooting production server! ..."
                    sh 'sudo reboot'
                }

                node ('staging') {
                    echo "Rebooting staging server! ..."
                    sh 'sudo reboot'
                }
                
            }
        }        

    }
}