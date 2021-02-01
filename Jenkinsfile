pipeline {
    agent any

    stages {
        stage('Build') {

            steps {
                sh 'npm install -g yarn'
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
