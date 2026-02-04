pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    dockerApp = docker.build("zaineamanda/learn-jenkins:${env.BUILD_ID}", "-f ./src/Dockerfile ./src")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-credentials') {
                        dockerApp.push('latest')
                        dockerApp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
        stage('Deploy on Kubernetes') {
            steps {
                echo 'Deploying...'
                // Add deploy steps here
            }
        }
    }
}