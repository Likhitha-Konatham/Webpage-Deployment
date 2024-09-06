pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                git 'https://github.com/d-Sujeeth/Jenkins-Pipeline.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    def image = docker.build("your-image-name:${env.BUILD_ID}")
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker container
                    docker.image("your-image-name:${env.BUILD_ID}").run('-d -p 8080:80')
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
    }
}
