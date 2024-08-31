pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/d-Sujeeth/Jenkins-Pipeline.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                // Add build commands here
                echo 'Building...'
            }
        }
        stage('Deploy') {
            steps {
                // Add deployment commands here
                echo 'Deploying...'
            }
        }
    }
}
