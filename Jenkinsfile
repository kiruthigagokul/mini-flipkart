pipeline {
    agent any

    environment {
        DOCKERHUB_USER = "crazykiruthi"
        IMAGE_NAME = "mini-flipkart-frontend"
    }

    stages {

        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pass', variable: 'DOCKERHUB_PASS')]) {
                    sh '''
                      echo $DOCKERHUB_PASS | docker login -u $DOCKERHUB_USER --password-stdin
                    '''
                }
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $DOCKERHUB_USER/$IMAGE_NAME:v1 frontend/'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKERHUB_USER/$IMAGE_NAME:v1'
            }
        }
    }
}

