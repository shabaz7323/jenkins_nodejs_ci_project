pipeline {
    agent any

    environment {
        IMAGE = "shabaz7323/jenkins-node-app"
        TAG = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Building Docker image: ${IMAGE}:${TAG}"
                bat "docker build -t %IMAGE%:%TAG% ."
                bat "docker tag %IMAGE%:%TAG% %IMAGE%:latest"
            }
        }
        stage('Login & Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASS')]) {
                    bat 'echo Logging in to Docker Hub...'
                    bat "docker login -u %DOCKERHUB_USER% -p %DOCKERHUB_PASS%"
                    bat "docker push %IMAGE%:%TAG%"
                    bat "docker push %IMAGE%:latest"
                }
            }
        }
    }

    post {
        success {
            echo "Docker image pushed: ${IMAGE}:${TAG}"
        }
        failure {
            echo "Build failed."
        }
    }
}
