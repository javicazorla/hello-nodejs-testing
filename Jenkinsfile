pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {
        stage('Build') {

            steps {
                sh 'yarn'
            }
        }

        stage('Test') {

            steps { 
                sh 'yarn run test'
                sh 'yarn run ci-test'
            }
        }
    }
}
