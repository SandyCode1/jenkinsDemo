pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SandyCode1/jenkinsDemo.git'
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                withAWS(credentials: 'your-aws-credentials-id', region: 'ap-south-1') {
                    sh '''
                        aws s3 sync . s3://your-bucket-name --delete
                    '''
                }
            }
        }
    }
}
