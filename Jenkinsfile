pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // To explicitly specify the branch and repository URL:
                git branch: 'main', url: "https://github.com/praveenrajt0413/application.git"
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Compiling code and running unit tests...'
               
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Packaging the application into a Docker container...'
                bat 'docker build -t praveen0210/java-test-app:latest .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying to Kubernetes...'
                bat 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
