pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-creds')
        DOCKER_IMAGE = 'soham1105/studentproject'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/soham1105/SohamC37_Django.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                sh 'echo $DOCKER_HUB_CREDENTIALS_PSW | docker login -u $DOCKER_HUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
