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
        stage('Build Docker Image') {
            steps {
                sh """
                    wget https://download.docker.com/linux/ubuntu/dists/bionic/pool/stable/amd64/docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                    dpkg -i ./docker-ce-cli_18.09.9~3-0~ubuntu-bionic_amd64.deb
                    apt-get update
                    apt-get install -y awscli
                    docker build -t workshopuser17:latest .
                    docker tag workshopuser17:latest workshopuser17:${BUILD_NUMBER}
                    docker tag workshopuser17:latest 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser17:latest

                    $(aws ecr get-login --region us-east-1 | sed 's/-e none//g')
                    docker push 686567993080.dkr.ecr.us-east-1.amazonaws.com/devopsbootcampuser17:latest
                """
            }
        }
        stage('DB Migrate') {
            steps {
                sh 'npm run migrate'
            }
        }
    }
}
