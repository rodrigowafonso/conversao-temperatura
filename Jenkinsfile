pipeline {
    agent any
    environment {
        HARBOR_URL = credentials('HARBOR_URL')
        HARBOR_PROJECT = credentials('HARBOR_PROJECT')
        HARBOR_CREDENTIALS = credentials('HARBOR_CREDENTIALS')
    }
    // Definir os stages
    stages {
        stage('Checkout do Código') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rodrigowafonso/conversao-temperatura.git']])
            }
        }     
        stage('Build Docker Image') {
            steps {
                sh 'echo "Executando o comando Docker Build"'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'echo "Executando o comando Docker Push"'
            }
        }

        stage('Deploy Docker Image') {
            steps {
                sh 'echo "Executando o comando Kubectl Apply"'
            }
        }
    }

}
