pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    stages {
        stage('Clone') {
            steps {
                // Clone the GitHub repository
                git url: 'https://github.com/ShadrackTanui/artillery.git'
            }
        }
        
        stage('Load Test') {
            steps {
                sh '/home/node/artillery/bin/run run /var/lib/jenkins/workspace/artillery-load-test/socket-io.yml'
            }
        }
    }
}
