pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-credentials')
        DOCKER_HUB_REPO = 'junaidjamshid/https://github.com/NUCESFAST/scd-final-lab-exam-JunaidJamshid123'
    }

    stages {
        stage('Checkout_1203') {
            steps {
                git branch: 'main', url: 'https://github.com/NUCESFAST/scd-final-lab-exam-JunaidJamshid123'
            }
        }
        stage('Install Dependencies_1203') {
            steps {
                script {
                    // Install dependencies for Auth service
                    dir('Auth') {
                        sh 'npm install'
                    }
                    // Repeat for other services as needed
                }
            }
        }
        stage('Build Docker Images_1203') {
            steps {
                script {
                    // Build Docker images for each service
                    dir('Auth') {
                        sh 'docker build -t auth-service .'
                    }
                    // Repeat for other services as needed
                }
            }
        }
        stage('Push Docker Images_1203') {
            steps {
                script {
                    // Login to Docker Hub
                    sh "echo ${DOCKER_HUB_CREDENTIALS_PSW} | docker login -u ${DOCKER_HUB_CREDENTIALS_USR} --password-stdin"

                    // Tag and push images to Docker Hub
                    sh 'docker tag auth-service ${DOCKER_HUB_REPO}/auth-service:latest'
                    sh 'docker push ${DOCKER_HUB_REPO}/auth-service:latest'

                    // Repeat for other services as needed
                }
            }
        }
    }
}
