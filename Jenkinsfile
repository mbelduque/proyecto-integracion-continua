pipeline {
    agent any

    tools {nodejs "node"}

    stages {
        stage('Git') {
            steps {
                git 'https://github.com/mbelduque/proyecto-integracion-continua.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh '<<Build Command>>'
            }
        }
        stage('Test') {
            steps {
                sh 'node test'
            }
        }
    }
}