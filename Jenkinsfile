pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    triggers {
        cron('0 0 * * *')
    }

    environment {
        AWS_ACCESS_KEY_ID = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }

    stages {
        stage('Set up Artillery Pro') {
            steps {
                sh 'npm install -g artillery-pro@latest'
            }
        }
        stage('Load Test on AWS') {
            steps {
                sh '/home/node/artillery/bin/run run-test --cluster artillery-pro-cluster --region us-east-1 --count 5'
            }
        }
    }
}
