pipeline {
  agent any

  environment {
    AWS_DEFAULT_REGION = 'us-east-1' // Change if needed
  }

  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/anki-9156/crm-project.git'
      }
    }

    stage('Deploy to S3') {
      steps {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-s3-creds']]) {
          sh 'aws s3 cp index.html s3://ank915/index.html'
        }
      }
    }
  }
}
