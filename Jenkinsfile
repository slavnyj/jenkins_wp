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
                    script {
                        try {
                            sh 'sudo reboot'
                        } catch (Exception e) {
                            echo 'Exception occurred: ' + e.toString()
                            echo "Production server is rebooted ..."
                        }
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
                    script {
                        try {
                            sh 'sudo reboot'
                        } catch (Exception e) {
                            echo 'Exception occurred: ' + e.toString()
                            echo "Staging server is rebooted ..."
                        }
                    }
                }
                
            }
        }

        stage ('Reboot both envs') {
            when {
                expression { params.ENV == 'BOTH' }
            }
            steps {
                node ('production') {
                    script {
                        try {
                            sh 'sudo reboot'
                        } catch (Exception e) {
                            echo 'Exception occurred: ' + e.toString()
                            echo "Production server is rebooted ..."
                        }
                    }
                }

                node ('staging') {
                    script {
                        try {
                            sh 'sudo reboot'
                        } catch (Exception e) {
                            echo 'Exception occurred: ' + e.toString()
                            echo "Staging server is rebooted ..."
                        }
                    }
                }
                
            }
        }        

    }
}