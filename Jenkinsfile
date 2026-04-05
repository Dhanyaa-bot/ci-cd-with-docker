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
               withCredentials([usernamePassword(credentialsId: '12f7e2ff-df45-4a38-aeb3-499270731b1b', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                sh 'echo $PASS | docker login -u $USER --password-stdin'
            }
        }
    }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
