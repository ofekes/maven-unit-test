pipeline {
    agent any
 
    stages {
        stage('Clean Workspace') {
            wrappers {
                preBuildCleanup {
                cleanupParameter('CLEANUP')
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -D clean test'
            }
 
            post {                
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success { allure([
                    includeProperties: true,
                    jdk: '',
                    properties: [[name: 'key1', value: 'value1'], [name: 'key2', value: 'value2']],
                    reportBuildPolicy: 'ALWAYS',
                    results: [[path: 'target/surefire-reports']]
                ])
            }
         }
    }
}      
}
