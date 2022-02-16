pipeline {
    agent {
        docker {
            image 'node:16-alpine'
            args '-p 3000:3000'
        }
    }
    environment { 
        CI = 'true'
    }
    stages {
        stage('Docker Build') {
            agent any
            steps {
                sh 'docker build -t ramkv/react-jenkins:latest .'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}