pipeline {
    agent any
 
    stages {
        stage('Test') {
            steps {
                cleanWs()
                checkout scm
            }
 
            post {                
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
               allure includeProperties: false, jdk: '', properties: [[key: 'allure.issues.tracker.pattern', value: 'https://etoro-jira.atlassian.net/browse/%s'], [key: 'allure.tests.management.pattern', value: 'https://github.com/eToro/DealingOps-FlowMatrix-Automation/']], results: [[path: 'allure-results']]
            }
         }
    }
}      
}
