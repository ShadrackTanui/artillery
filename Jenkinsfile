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
                sh '/usr/local/bin/artillery/bin run /var/lib/jenkins/workspace/artillery-load-test/socket-io.yml'
            }
        }
    }
}
