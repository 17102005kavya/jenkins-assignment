pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-frontend-app"
        CONTAINER_NAME = "frontend-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/17102005kavya/jenkins-assignment.git'
            }
        }

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
