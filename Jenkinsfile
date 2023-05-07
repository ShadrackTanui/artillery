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
                sh '/home/node/artillery/bin/run run https://github.com/ShadrackTanui/artillery'
            }
        }
    }
}
