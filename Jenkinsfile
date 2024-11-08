pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Replace 'main' with 'master' if that is your default branch
                git branch: 'main', url: 'https://github.com/arunkumar13082004/react-jenkins-docker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Replace 'your-username' with your actual Docker Hub or registry username
                    docker.build("arunkumar13082004/react-app:${env.BUILD_ID}")
                }
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                script {
                    // Ensure Docker Compose is set up correctly and the docker-compose.yml file is in the root directory
                    sh 'docker-compose down'
                    sh 'docker-compose up -d'
                }
            }
        }
    }
    post {
        always {
            script {
                // Ensure this cleanup command works if the Docker Compose setup is running
                sh 'docker-compose down'
            }
        }
    }
}
