pipeline {
    agent any
    environment {
        HARBOR_URL = credentials('HARBOR_URL')
        HARBOR_PROJECT = credentials('HARBOR_PROJECT')
        HARBOR_CREDENTIALS = credentials('HARBOR_CREDENTIALS')
        IMAGE_NAME = credentials('IMAGEM_NAME')
        IMAGE_TAG = credentials('IMAGE_TAG')
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
                script {
                    dir('src') {
                        dockerImage = docker.build("${HARBOR_URL}/${HARBOR_PROJECT}/${IMAGE_NAME}:${IMAGE_TAG}")
                    }
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://harbor.focopontovirtual.com.br','HARBOR_CREDENTIALS') {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        cleanup {
            sh 'docker system prune -f'
        }
    }
}
