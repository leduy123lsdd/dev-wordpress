pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        
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
                echo "this is my docker account: $DOCKER_ACCOUNT_USR"
                echo "this is my docker password account: $DOCKER_ACCOUNT_PSW"
                '''
            }
        }
        


    }
}
