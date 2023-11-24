pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git 'https://github.com/himanshuhsk01/pipeline.git'
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    bat(script: 'javac Main.java', returnStatus: true) // Use 'bat' on Windows
                    
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    bat(script: 'java Main', returnStatus: true) // Use 'bat' on Windows
                    
                }
            }
        }
    }
    
    post {
        success {
            echo 'Build successful!'
        }
        
        failure {
            echo 'Build failed!'
        }
    }
}
