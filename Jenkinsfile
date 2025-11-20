pipeline {
    agent any
    
    tools {
        nodejs 'Node16'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully. (Not starting server)'
            }
        }
    }

    post {
        success {
            echo 'Pipeline Success'
        }
    }
}
