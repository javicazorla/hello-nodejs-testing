pipeline {
    agent any

    stages {
        stage('Build') {

            steps { 
                sh 'yarn'
                sh 'yarn install'
            }
        }

        stage('Test') {

            steps { 
                sh 'yarn run test'
            }
        }
    }
}
