pipeline {
        environment {
            registry = "ramkumarv93/samplereactapp"
            registryCredential = 'dockerhub'
            dockerImage = ''
        }
        agent any
        stage('Building our image') {
        steps{
            script {
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
        }
    }
        stage('Deploy our image') {
            steps{
                script {
                    docker.withRegistry( '', registryCredential ) {
                    dockerImage.push()
                }
            }
        }
    }
        stage('Cleaning up') {
            steps{
                sh "docker rmi $registry:$BUILD_NUMBER"
            }
        }
}