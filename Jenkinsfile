pipeline {
    agent any
    environment {
        AWS_REGION = 'ap-south-1'
        ECR_REPO   = '123456789.dkr.ecr.ap-south-1.amazonaws.com'
        IMAGE_TAG  = "${BUILD_NUMBER}-${GIT_COMMIT[0..6]}"
    }
    stages {
        stage('Build') { ... }
        stage('SonarQube Scan') { ... }
        stage('ECR Push') { ... }
        stage('Deploy → Dev') { ... }
        stage('Approval: Dev → Staging') {
            steps {
                input message: 'Deploy to Staging?', ok: 'Proceed'
            }
        }
        stage('Deploy → Staging') { ... }
        stage('Approval: Staging → Prod') {
            steps {
                input message: 'Deploy to Production?', ok: 'Proceed'
            }
        }
        stage('Deploy → Prod') { ... }
    }
}
