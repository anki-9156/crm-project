pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/anki-9156/crm-project.git'
            }
        }

        stage('Upload to S3') {
            steps {
                // This uses the S3 plugin's configured profile
                s3Upload(
                    bucket: 'ank915',
                    path: '/',
                    file: 'index.html',
                    profileName: 'aws-s3-profile', // replace with your actual profile name if it's not 'default'
                    acl: 'PublicRead'
                )
            }
        }
    }
}
