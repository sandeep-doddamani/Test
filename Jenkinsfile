pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Pull the latest Nginx image
                    sh 'docker pull nginx:latest'
                    // Build the Docker image
                    sh 'docker build -t my-nginx-image .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Remove any existing container named my-nginx
                    sh 'docker rm -f my-nginx || true'
                    // Run the Docker container
                    sh 'docker run -d --name my-nginx -p 80:80 my-nginx-image'
                }
            }
        }
    }
    post {
        always {
            // Clean up any images or containers after the build
            sh 'docker rmi my-nginx-image || true'
        }
    }
}
