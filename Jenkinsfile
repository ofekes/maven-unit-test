pipeline {
    agent any
 
    stages {
        stage('Test') {
            steps {
                cleanWs()
                checkout scm
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
