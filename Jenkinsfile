pipeline {
    agent any 

    environment {
        BUILD_PATH = '/var/lib/jenkins/build-wordpress-container'
    }

    stages {

        stage('Build') { 
            steps {
                script {
                    withCredentials([
                        usernamePassword(credentialsId: 'jenkins', usernameVariable: 'jenkins-user', passwordVariable: 'jenkins-pass')
                    ]) {
                        print 'jenkins-user=' + jenkins-user + ' password=' + jenkins-pass
                        print 'username.collect { it }=' + jenkins-user.collect { it }
                        print 'password.collect { it }=' + jenkins-pass.collect { it }
                    }
                }
            }
        }


    }
}