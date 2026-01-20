pipeline {
    agent any
    
    environment {
        DOCKER_USER = 'ordoron'
        IMAGE_NAME = 'my-flask-app'
        PROD_IP = '18.196.246.145'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh "docker build -t ${DOCKER_USER}/${IMAGE_NAME}:latest ."
                    sh "echo \$PASS | docker login -u \$USER --password-stdin"
                    sh "docker push ${DOCKER_USER}/${IMAGE_NAME}:latest"
                }
            }
        }

        stage('Deploy to Prod') {
            steps {
                sshagent(['prod-ssh-key']) {
                    sh "ssh -o StrictHostKeyChecking=no ubuntu@${PROD_IP} 'cd ~/prod-deployment && docker compose pull && docker compose up -d'"
                }
            }
        }
    }
}
