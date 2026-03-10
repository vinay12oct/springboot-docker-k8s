pipeline {
    agent any

    environment {
        IMAGE_NAME = "vinay12oct/springboot-docker-demo"
        IMAGE_TAG = "2.0"
    }

    stages {

        stage('Build Application') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME%:%IMAGE_TAG% .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push %IMAGE_NAME%:%IMAGE_TAG%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl set image deployment/springboot-deployment springboot-container=%IMAGE_NAME%:%IMAGE_TAG%'
            }
        }
    }
}