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
                sh '/home/node/artillery/bin/run report --output reports/report reports/report.json'
                sh 'npm install -g artillery-reports'
                sh 'artillery-reports report reports/report.json reports/report.html'
                sh 'npm install -g pdfkit'
                sh 'node -e "const PDFDocument = require(\'pdfkit\'); const fs = require(\'fs\'); const doc = new PDFDocument(); doc.pipe(fs.createWriteStream(\'reports/report.pdf\')); doc.font(\'Helvetica\').fontSize(12).text(fs.readFileSync(\'reports/report.html\', \'utf8\')); doc.end();"'
            }
        }
    }
    post {
        success {
            archiveArtifacts 'reports/*'
        }
    }
}
