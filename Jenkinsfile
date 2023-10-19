pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }



        stage('Run Postman Tests') {
            steps {
               bat 'newman run "Dog API Test.postman_collection.json"--reporter-junit-export test-report.xml --reporter-html-export test-report.html'
            }
        }
    }

    post {
        success {
            publishHTML target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: 'newman',
                reportFiles: 'index.html',
            ]
           

        }
    }
}
