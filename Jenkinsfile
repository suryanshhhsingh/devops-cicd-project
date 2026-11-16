
pipeline {
    agent any

    environment {
        APP_NAME = 'devops-app'
        KUBECONFIG = 'C:\\Users\\USER\\.kube\\config'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/suryanshhhsingh/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app:v1 ./application'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f kubernetes/deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl rollout status deployment/devops-app'
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
    }
}
