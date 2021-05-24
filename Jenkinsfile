pipeline {
    agent any
    tools {
        nodejs 'rjnode'
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }   
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Sonar Scan') {
            steps {
                withSonarQubeEnv('rjsonar') {
                    //hudson.plugins.sonar.SonarRunnerInstallation('rjsonarscanner')
                    sh 'printenv'
                }
            }
        }
    }
}
