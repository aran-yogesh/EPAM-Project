pipeline {
    agent any

    stages {
        stage('Import Jenkinsfile') {
            steps {
                bat 'git clone https://github.com/aran-yogesh/EPAM-Project.git'
            }
        }
        stage('Code') {
            steps {
                echo 'Code successfull'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Build Successfull'
            }
        }
        
        stage('Image and push image') {
            steps {
                echo 'Push Successfull'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploy Successfull'
            }
        }
    }
}
