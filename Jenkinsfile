pipeline {
    agent any
    stages {
        stage("Code Clone") {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sakibshaikh7860/jenkins-demo.git'
            }
        }
        stage("Build") {
            steps {
                echo "Code build ho raha hai..."
                sh "cat index.html"
            }
        }
        stage("Test") {
            steps {
                echo "Tests run ho rahe hain..."
                sh "echo 'All tests passed!'"
            }
        }
        stage("Deploy") {
            steps {
                echo "Deploy ho raha hai..."
                sh "echo 'Deployed successfully!'"
            }
        }
    }
    post {
        success { echo "Pipeline SUCCESS!" }
        failure { echo "Pipeline FAILED!" }
    }
}
