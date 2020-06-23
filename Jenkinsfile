pipeline {
    agent {
        docker {
            image 'node:12.10.0-alpine'
            args '-p 80:80'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Git') {
            steps {
                git 'https://github.com/mbelduque/proyecto-integracion-continua.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'node test'
            }
        }
    }
}