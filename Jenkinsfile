pipeline {
    agent any

    stages {
        stage('Import Jenkinsfile') {
            steps {
                git 'git clone https://github.com/aran-yogesh/EPAM-Project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t my-flask-app . '
            }
        }

        stage('Test') {
            steps {
                sh 'docker run -d --name flask-app -p 5000 my-flask-app'
            }
        }

        stage('Login and Push Image') {
            steps {
                sh 'python3 ecr.py'
                sh 'python3 eks.py'
                sh 'docker tag my-flask-app:latest 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-flask-app:latest'
                sh 'docker push 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-flask-app:latest'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
                sh 'kubectl port-forward svc/my-flask-service 5000:5000'
            }
        }
    }
}
