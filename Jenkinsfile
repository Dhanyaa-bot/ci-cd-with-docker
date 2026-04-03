pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "dhanya1/app"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Dhanyaa-bot/ci-cd-with-docker.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                sh 'echo dhanyabhat1  | docker login -u dhanyabhat  --password-stdin'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
