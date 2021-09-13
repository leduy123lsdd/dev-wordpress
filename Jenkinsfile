pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        MY_SECRET = credentials('my_secret_text')
        
        DOCKER_ACCOUNT = credentials('docker_account')
    }

    stages {

        stage('Build') { 
            steps {
                sh '''
                echo "this is my secret: $MY_SECRET"
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
