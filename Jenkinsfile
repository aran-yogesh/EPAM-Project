pipeline {
    agent any

    stages {
        stage('Import Jenkinsfile') {
            steps {
                bat 'git clone https://github.com/aran-yogesh/EPAM-Project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'docker build -t my-flask-app .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run my-flask-app python3 test.py'
            }
        }

        stage('Login and Push Image') {
            steps {
                bat 'python3 ecr.py'
                bat 'python3 eks.py'
                bat 'docker tag my-flask-app:latest 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-flask-app:latest'
                bat 'docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-flask-app:latest'
            }
        }

        stage('Deploy') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
                bat 'kubectl apply -f k8s/service.yaml'
                bat 'kubectl port-forward svc/my-flask-service 5000:5000'
            }
        }
    }
}
