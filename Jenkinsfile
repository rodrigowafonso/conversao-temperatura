pipeline {
    agent any

    // Definir os stages
    stages {
        stage('Build Docker Image') {
            stepes {
                sh 'echo "Executando o comando Docker Build"'
            }
        }

        stage('Push Docker Image') {
            stepes {
                sh 'echo "Executando o comando Docker Push"'
            }
        }

        stage('Deploy Docker Image') {
            stepes {
                sh 'echo "Executando o comando Kubectl Apply"'
            }
        }
    }

}