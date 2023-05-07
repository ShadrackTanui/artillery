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
                sh '/usr/local/bin/artillery/bin run tests/performance/socket-io.yml'
            }
        }
    }
}
