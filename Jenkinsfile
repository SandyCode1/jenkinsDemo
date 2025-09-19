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
                withAWS(credentials: '9bec421a-2287-4cea-b192-56e525635dbc', region: 'ap-south-1') {
                    sh '''
                        aws s3 sync . s3://jenkinsdemo-negi --delete
                    '''
                }
            }
        }
    }
}
