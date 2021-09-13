pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        
        // pull image with secret name 
        MY_SECRET_IMAGE = credentials('secret_docker_image')
        
        DOCKER_ACCOUNT = credentials('docker_account')
    }

    stages {

        stage('Down load image') { 
            steps {
                ansiblePlaybook($BUILD_PATH + '/credential-ansible.yml') {
                    inventoryPath($BUILD_PATH + '/inventory.txt')
                    extraVars {
                        extraVar("docker_user", $DOCKER_ACCOUNT_USR)
                        extraVar("docker_pass", $DOCKER_ACCOUNT_PSW)
                    }
                }
            }
        }
        
        stage('Login docker hub ') { 
            steps {
                sh '''
                docker login --username=$DOCKER_ACCOUNT_USR --password=$DOCKER_ACCOUNT_PSW
                '''
            }
        }
        


    }
}
