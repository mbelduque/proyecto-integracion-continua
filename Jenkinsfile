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
        stage('Initialize') {
            def dockerHome = tool 'MyDocker'
            env.PATH = "${dockerHome}/bin:${env.PATH}"
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)?'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}