pipeline {
    agent any

    environment {
        APP_NAME = 'production-node-app'
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    sh "docker build -t ${APP_NAME}:${IMAGE_TAG} ."
                }
            }
        }

        stage('Security & Audit') {
            steps {
                echo 'Running vulnerability check...'
                sh 'npm audit --audit-level=high || true'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo "Jenkins build #${env.BUILD_NUMBER} completed successfully."
        }
        failure {
            echo "Jenkins build #${env.BUILD_NUMBER} failed."
        }
    }
}