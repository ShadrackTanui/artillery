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

    stages {
        stage('Load Test') {
            steps {
                sh '/home/node/artillery/bin/run run --output reports/report.json tests/performance/socket-io.yaml'
                sh '/home/node/artillery/bin/run report --output reports/report reports/report.json'
            }
        }
    }

    post {
        success {
            archiveArtifacts 'reports/*'
        }
    }
}
