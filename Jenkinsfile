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
               bat 'newman run "Dog API Test.postman_collection.json"'
            }
        }
    }

    post {
        success {
            publishHTML target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: 'C:\Users\L3NY\AppData\Local\Jenkins\.jenkins\workspace',
                reportFiles: 'index.html',
            ]
           

        }
    }
}
