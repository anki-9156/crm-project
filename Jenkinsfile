pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'ap-south-1' // change if needed
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
                    sh '''
                        echo "Uploading index.html to S3..."
                        aws s3 cp index.html s3://ank915/index.html --acl public-read
                    '''
                }
            }
        }
    }
}
