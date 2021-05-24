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
//                    sh "${tool("rjsonarscanner")}/bin/sonar-scanner -Dsonar.login=489fa9c26a3f6e0704855481ee5c89876e7ba9b4"
                    sh "${tool("rjsonarscanner")}/bin/sonar-scanner"
                }
            }
        }
    }
}
