pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
        MY_SECRET = credentials('my_secret_text')
    }

    stages {

        stage('Build') { 
            steps {
                sh '''
                echo "this is my secret: $MY_SECRET"
                '''
            }
        }


    }
}
