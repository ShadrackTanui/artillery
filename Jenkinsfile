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
                sh '/home/node/artillery/bin/run run --output reports/report.json /var/lib/jenkins/workspace/artillery-load-test/haproxy2.yml'
                
            }
        }
    }
    post {
        success {
            archiveArtifacts 'reports/*'
        }
    }
}
