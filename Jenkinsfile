pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                nodejs('mattnode') {
                    sh 'npm install'
                }
              
            }
        }
    }
}
