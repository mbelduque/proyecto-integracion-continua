pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Cloning Git') {
            steps {
                git 'https://github.com/mbelduque/proyecto-integracion-continua.git'
            }
        }
        stage('Building image') {
            steps{
                script {
                    docker build -t template-shop:1.0 .
                }
            }
        }
    }
}