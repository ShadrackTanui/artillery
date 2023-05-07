pipeline {
    agent {
        label "docker" {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    stages {
        stage('Load Test') {
            steps {
                sh '/home/node/artillery/bin/run run tests/performance/socket-io.yml'
            }
        }
    }
}
