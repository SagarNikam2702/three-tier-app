pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/SagarNikam2702/three-tier-app.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                bat 'docker build -t sagarnikam2702/three-tier-backend:v1 backend'
            }
        }

        stage('Build Frontend Image') {
            steps {
                bat 'docker build -t sagarnikam2702/three-tier-frontend:v1 frontend'
            }
        }

        stage('Push Backend Image') {
            steps {
                bat 'docker push sagarnikam2702/three-tier-backend:v1'
            }
        }

        stage('Push Frontend Image') {
            steps {
                bat 'docker push sagarnikam2702/three-tier-frontend:v1'
            }
        }

        stage('Deploy') {
            steps {
                bat 'kubectl apply -f k8s/'
            }
        }
    }
}