pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Git checkout successful'
            }
        }

        stage('Build') {
            steps {
                bat 'echo Build successful'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Tests completed'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t jenkins-cicd-demo .'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}
