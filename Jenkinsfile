pipeline {
    agent any

    tools {
        nodejs 'nodejs-14.15.4'
    }

    stages {
        stage('Build') {

            steps {
                sh 'yarn install'
            }
        }

        stage('Test') {

            steps { 
                sh 'yarn run test'
                sh 'yarn run ci-test'
            }
            post {
                always {
                    step([$class: "TapPublisher", testResults: "test.tap"])
                    step([
                        $class: 'CloverPublisher',
                        cloverReportDir: 'coverage',
                        cloverReportFileName: 'clover.xml',
                        healthyTarget: [methodCoverage: 70, conditionalCoverage: 80, statementCoverage: 80], // optional, default is: method=70, conditional=80, statement=80
                        unhealthyTarget: [methodCoverage: 50, conditionalCoverage: 50, statementCoverage: 50], // optional, default is none
                        failingTarget: [methodCoverage: 0, conditionalCoverage: 0, statementCoverage: 0]     // optional, default is none
  ])
                }
            }

        }
        stage("Trivy Scan"){
            steps{
                sh 'trivy image --format json --output trivy-results.json debian:10.8'
            }
            post {
                always {
                    recordIssues(
                    enabledForFailure: true,
                    tool: trivy(pattern: '*.json')
                    )
                }
            }
        }
    }
}
