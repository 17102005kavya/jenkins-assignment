pipeline {
    agent any

    environment {
        IMAGE_NAME = "2023bcs0082/simple-frontend-app"
        CONTAINER_NAME = "frontend-container"
    }

    stages {

     
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
