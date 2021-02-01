pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
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
                    step([$class: "TapPublisher", testResults: "**/test/tap-unit.log"])
                }
            }

        }
    }
}
