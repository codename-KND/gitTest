pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Newman') {
            steps {
                sh 'npm install -g newman'
            }
        }

        stage('Run Postman Tests') {
            steps {
                sh 'newman run Dog API Test.postman_collection.json'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '**/newman/**', allowEmptyArchive: true
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
