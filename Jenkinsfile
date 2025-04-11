pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/anki-9156/crm-project.git'
            }
        }

        stage('Upload index.html to S3') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-s3-creds']]) {
                    sh 'aws s3 cp index.html s3://ank915/index.html --acl public-read'
                }
            }
        }
    }
}
