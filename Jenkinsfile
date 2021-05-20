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
        stage('Sonar') {
            tool name: 'MattScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
            steps {
                withSonarQubeEnv {
                 // some block
                }
              
            }
        }
    }
}
