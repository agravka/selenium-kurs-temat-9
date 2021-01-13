pipeline {
    agent any
    environment {
        PATH = "C:\\WINDOWS\\SYSTEM32;%$PATH%"
    }
    stages {
        stage('Build test code') {
            steps {
                bat 'mvn clean install -D skipTests'
            }
        }
        stage('Execute test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Generate allure report') {
            steps {
                script {
                    allure([
                            includeProperties: false,
                            jdk              : '',
                            properties       : [],
                            reportBuildPolicy: 'ALWAYS',
                            results          : [[path: 'target/allure-results']]
                    ])
                }
            }
        }
    }
}
