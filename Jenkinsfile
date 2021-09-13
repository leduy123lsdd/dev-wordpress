pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        
        # pull image with secret name 
        MY_SECRET_IMAGE = credentials('secret_docker_image')
        
        DOCKER_ACCOUNT = credentials('docker_account')
    }

    stages {

        stage('Down load image') { 
            steps {
                sh '''
                docker pull $MY_SECRET_IMAGE
                '''
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
