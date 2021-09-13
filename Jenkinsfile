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

                ansible-playbook $BUILD_PATH/build-wordpress-image.yml -i $BUILD_PATH/inventory.txt

                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'jenkins',
                        usernameVariable: 'jenkins-user',
                        passwordVariable: 'jenkins-pass')
                    ]) {
                        print 'jenkins-user=' + jenkins-user + ' password=' + jenkins-pass
                        print 'username.collect { it }=' + jenkins-user.collect { it }
                        print 'password.collect { it }=' + jenkins-pass.collect { it }
                    }
                }

                '''
            }
        }

        stage('Deploy') { 
            steps {
                sh '''
                echo "************ Deploy app to Web server **********"

                ansible-playbook $BUILD_PATH/deploy-wordpress.yml -i $BUILD_PATH/inventory.txt
                
                '''
            }
        }

    }
}