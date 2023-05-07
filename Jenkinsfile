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
                withArtillery(jdk: '11') {
                    sh '/home/node/artillery/bin/run run --output reports/report.json tests/performance/socket-io.yaml'
            }
        }
    }
}
}
