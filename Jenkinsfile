pipeline {
    agent any
    stages {
        stage('Commit') {
            steps {
                sh './gradlew clean assemble'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew clean check'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'build/reports/tests/test/', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
                junit 'build/test-results/tests/*.xml'
            }
        }
        stage('Package') {
            steps {
                sh './gradlew clean shadowJar'
            }
        }
    }
}
