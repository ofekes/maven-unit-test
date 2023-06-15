pipeline {
    agent any
 
    stages {
        stage('Test') {
            steps {
                sh 'mvn -D clean test'
            }
 
            post {                
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success { allure([
                    includeProperties: false,
                    jdk: '',
                     properties: [Environment="Ofer Test"],
                    reportBuildPolicy: 'ALWAYS',
                    results: [[path: 'target/surefire-reports']]
                ])
            }
         }
    }
}      
}
