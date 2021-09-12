pipeline {
    agent any 
    stages {

        stage('Build') { 
            steps {
                sh '''
                echo "************ Containerizing app to docker image **********"
                echo "************ Containerizing app to docker image **********"
                echo "************ Containerizing app to docker image **********"
                ansible-playbook /home/vagrant/deploy-web/playbook-pingtest.yml -i /home/vagrant/deploy-web/inventory.txt
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