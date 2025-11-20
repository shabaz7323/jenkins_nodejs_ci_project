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
                bat 'node app.js'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
    }
}
