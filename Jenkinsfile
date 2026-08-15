pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = '123456789012'
        AWS_REGION     = 'us-east-1'
        ECR_REPO_NAME  = 'sample-node-app'
        IMAGE_TAG      = "${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Unit Tests') {
            steps {
                dir('App') {
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }

        stage('Docker Build & Security Scan') {
            steps {
                sh "docker build -t ${ECR_REPO_NAME}:${IMAGE_TAG} ."
                sh "trivy image --severity HIGH,CRITICAL ${ECR_REPO_NAME}:${IMAGE_TAG}"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}