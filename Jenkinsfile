pipeline {
    agent any
 
    stages {
        stage('Test') {
            steps {
                cleanWs()
                checkout scm
                allure includeProperties: false, jdk: '', properties: [[key: 'allure.issues.tracker.pattern', value: 'https://etoro-jira.atlassian.net/browse/%s'], [key: 'allure.tests.management.pattern', value: 'https://github.com/eToro/DealingOps-FlowMatrix-Automation/']], results: [[path: 'allure-results']]

            }
         }
    }
}
