pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t adhamgamal74/web-server:$BUILD_NUMBER .'
            }
        }

        stage('Push') {    
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push adhamgamal74/web-server:$BUILD_NUMBER '
                }
            }
        }
    }
}
