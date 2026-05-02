pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "sakibshaikh7840/jenkins-demo-app"
    }
    stages {
        stage("Code Clone") {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sakibshaikh7860/jenkins-demo.git'
            }
        }
        stage("Docker Build") {
            steps {
                sh "docker build -t ${DOCKER_IMAGE}:${BUILD_NUMBER} ."
            }
        }
        stage("Docker Push") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh "echo ${DOCKER_PASS} | docker login -u ${DOCKER_USER} --password-stdin"
                    sh "docker push ${DOCKER_IMAGE}:${BUILD_NUMBER}"
                }
            }
        }
        stage("Docker Run") {
            steps {
                echo "deploying contaner"
		sh "docker-compose down && docker-compose up -d"
            }
        }
    }
    post {
        success { echo "App deployed! Visit http://localhost:8090" }
        failure { echo "Pipeline FAILED!" }
    }
}
