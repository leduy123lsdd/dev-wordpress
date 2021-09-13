pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        
        // pull image with secret name 
        MY_SECRET_IMAGE = credentials('secret_docker_image')
        
        DOCKER_ACCOUNT = credentials('docker_account')
        
        DOCKER_HUB_IMAGE = credentials('secret_docker_image')
    }

    stages {

        stage('Build image') { 
            steps {
                sh '''
                docker build -t $DOCKER_HUB_IMAGE .
                '''
            }
        }
        
        stage('Push image to docker hub ') { 
            steps {
                ansiblePlaybook(
                    inventory: '$BUILD_PATH/inventory.txt',
                    playbook: '$BUILD_PATH/build-wordpress-image.yml',
                    extraVars: [
                        DOCKER_USER: '$DOCKER_ACCOUNT_USR',
                        DOCKER_PASS: '$DOCKER_ACCOUNT_PSW',
                        DOCKER_HUB_IMAGE: '$DOCKER_HUB_IMAGE'
                    ]
                )
            }
        }
        
        stage('Deploy web server ') { 
            steps {
                sh '''
                echo "************ Deploy app to Web server **********"

                ansible-playbook $BUILD_PATH/deploy-wordpress.yml -i $BUILD_PATH/inventory.txt
                
                '''
            }
        }
       
    }
}
