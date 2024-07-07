pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        S3_BUCKET = 'your-s3-bucket-name'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git 'https://github.com/your-username/static-website-jenkins.git'
            }
        }
        stage('Build') {
            steps {
                // Echo statement for the build step
                echo 'Building the website...'
                // Add actual build steps if needed
            }
        }
        stage('Test') {
            steps {
                // Echo statement for the test step
                echo 'Running tests...'
                // Add actual test steps if needed
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy to S3 bucket using AWS CLI
                    sh '''
                    aws s3 sync . s3://$S3_BUCKET --exclude ".git/*" --delete
                    '''
                }
            }
        }
    }

    post {
        success {
            // Echo statement for successful deployment
            echo 'Deployment successful!'
        }
        failure {
            // Echo statement for failed deployment
            echo 'Deployment failed!'
        }
    }
}
