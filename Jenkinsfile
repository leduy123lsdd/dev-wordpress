pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
    }

    stages {

        stage('Build') { 
            steps {
                sh '''
                echo "************ Containerizing app to docker image **********"

                

                docker build -t duy123galaxy13/wordpress .
                docker tag duy123galaxy13/wordpress duy123galaxy13/wordpress:latest

                ansible-playbook $BUILD_PATH/build-wordpress-image.yml -i $BUILD_PATH/inventory.txt

                '''
            }
        }

        stage('Deploy') { 
            steps {
                sh '''
                echo "************ Deploy app to Docker Hub **********"

                ansible-playbook $BUILD_PATH/deploy-wordpress.yml -i $BUILD_PATH/inventory.txt
                
                '''
            }
        }

    }
}