pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'
        jdk 'jdk11'
    }
    stages {
        stage ('pull from git') {
            steps {
                git 'https://github.com/mfaruk/cucumber-report-pipeline.git'
                sh 'ls'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean install test'

            cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'
                
            }
        }
    }
}
