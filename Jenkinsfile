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
                //sh 'cd Maven-pipeline'
                sh 'mvn clean install test'
                //cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', 
pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
            cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'
                
            }
        }
    }
}
