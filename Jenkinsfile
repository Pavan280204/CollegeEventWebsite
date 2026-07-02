pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Pavan280204/CollegeEventWebsite.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t college-event .'
            }
        }

        stage('Start Minikube') {
    steps {
        bat 'whoami'
        bat 'echo %USERPROFILE%'
        bat 'dir C:\\Users\\nukal\\.minikube'
        bat 'minikube profile list'
    }
}

        stage('Load Image into Minikube') {
            steps {
                bat 'minikube image load college-event:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
    }
}