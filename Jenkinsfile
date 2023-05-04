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
                bat echo "build successful"
            }
        }

        stage('Test') {
            steps {
                bat echo "test successful"
            }
        }

        stage('Login and Push Image') {
            steps {
                bat "login and push successful"
            }
        }

        stage('Deploy') {
            steps {
                bat echo "Deploy succesfull"
        }
    }
}
