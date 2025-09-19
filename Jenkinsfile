pipeline {
    agent any

    //triggers {
        //pollSCM('H/2 * * * *')  // check every 2 minutes
    //}

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SandyCode1/jenkinsDemo.git'
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                withAWS(credentials: '9bec421a-2287-4cea-b192-56e525635dbc', region: 'ap-south-1') {
                    bat '''
                        aws s3 sync . s3://jenkinsdemo-negi --delete
                    '''
                }
            }
        }
    }
}
