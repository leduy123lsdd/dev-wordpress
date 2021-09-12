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

                // docker rmi my-wordpress-image

                docker build -t my-wordpress-image .

                // ansible-playbook $BUILD_PATH/playbook-pingtest.yml -i $BUILD_PATH/inventory.txt



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