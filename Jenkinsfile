pipeline {
    agent any

    environment {
        // Define environment variables if needed
        DOCKER_HUB_CREDENTIALS = 'bf153ce8-4048-4ca4-b781-830c87ec605b'
        DOCKER_IMAGE_NAME = 'ranjeet6/your-java-app'
        DOCKER_IMAGE_TAG = "${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the Git repository
                checkout scm
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    def dockerImage = docker.build("${DOCKER_IMAGE_TAG}")

                    // Authenticate with Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', "${DOCKER_HUB_CREDENTIALS}") {
                        // Push the Docker image to Docker Hub
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo "Docker image built and pushed successfully"
        }
    }
}
