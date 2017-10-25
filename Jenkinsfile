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
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'build/reports/tests/test/', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: 'HTML Report'])
                junit 'build/test-results/test/*.xml'
            }
        }
        stage('Package') {
            steps {
                sh './gradlew clean shadowJar'
                archive 'build/libs/*'
            }
        }
    }
}
