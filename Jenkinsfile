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
                sh '/home/node/artillery/bin/run run --output reports/report.pdf /var/lib/jenkins/workspace/artillery-load-test/haproxy2.yml'
                sh '/home/node/artillery/bin/run report --output reports/report reports/report.pdf'
            }
        }
    }
    post {
        success {
            archiveArtifacts 'reports/*'
        }
    }
}
