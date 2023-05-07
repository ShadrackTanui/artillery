pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    stages {
        stage('Load Test') {
            steps {
                sh '/home/node/artillery/bin/run run --output reports/report.json tests/performance/socket-io.yaml'
            }
        }
    }
}
