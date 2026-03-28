pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Compiling code and running unit tests...'
                // If the Jenkinsfile is in the 'application' folder, and the application folder is your repo root,
                // we don't need the dir('application') block anymore.
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
