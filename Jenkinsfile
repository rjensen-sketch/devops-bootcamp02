pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs('mattnode') {
                    sh 'npm install'
                }
              
            }
        }   
        stage('Test') {
            steps {
                nodejs('mattnode') {
                    sh 'npm test'
                }
              
            }
        }
    }
}
