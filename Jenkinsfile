pipeline {
    agent any 

    environment {
        BUILD_PATH = '/home/vagrant/deploy-web'
    }

    stages {

        stage('Build') { 
            steps {
                sh '''
                echo "************ Containerizing app to docker image **********"
                docker build -t my-wordpress-image .
                
                '''
            }
        }

        stage('Deploy') { 
            steps {
                sh '''
                echo "************ Deploy app to Docker Hub **********"
                '''
            }
        }

    }
}