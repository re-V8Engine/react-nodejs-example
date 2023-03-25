pipeline {
    agent any
    stages {
        stage('Login to DockerHub') {
            steps{
                echo 'Logging in to DockerHub...'
                withCredentials([usernamePassword(credentialsId: dockerhub-credentials, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                }
            }
        }
        stage('Build Docker image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t v8engine/react-nodejs-example:1.0 .'
            }
        }
        stage('Push Docker image to DockerHub repo')
        {
            echo "Pushing Docker image to DockerHub repo..."
            sh 'docker push v8engine/react-nodejs-example'
        }
    }
}