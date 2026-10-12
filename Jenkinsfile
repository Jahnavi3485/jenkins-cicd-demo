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
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Jenkins pipeline completed successfully.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}\nCheck: ${env.BUILD_URL}",
                to: "karthikpalumari7@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Jenkins pipeline failed.\nJob: ${env.JOB_NAME}\nBuild: ${env.BUILD_NUMBER}\nCheck: ${env.BUILD_URL}",
                to: "karthikpalumari7@gmail.com"
            )
        }
    }
}
