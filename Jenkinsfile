pipeline {
    agent any
    stages {
        stage("Code Clone") {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sakibshaikh7860/jenkins-demo.git'
            }
        }
        stage("Docker Build") {
            steps {
                sh "docker build -t jenkins-demo-app ."
            }
        }
	stage("Notify"){
	    steps {
		echo "Build complate,Tell to team"
	     }
	}
        stage("Docker Run") {
            steps {
                sh "docker stop jenkins-demo || true"
                sh "docker rm jenkins-demo || true"
                sh "docker run -d --name jenkins-demo -p 8090:80 jenkins-demo-app"
            }
        }
    }
    post {
        success { echo "App deployed! Visit http://localhost:8090" }
        failure { echo "Pipeline FAILED!" }
    }
} 
