pipeline {
    agent any

    stages {
        stage('Build') {

            steps {
                sh 'yarn install'
                sh 'yarn'
            }
        }

        stage('Test') {

            steps { 
                sh 'yarn run test'
            }
        }
    }
}
