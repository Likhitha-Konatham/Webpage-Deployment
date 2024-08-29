pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository
                git 'https://github.com/d-Sujeeth/Jenkins-Pipeline/index.html'
            }
        }

        stage('Run HTML Code') {
            steps {
                // Start a simple HTTP server to run HTML code
                sh 'python -m http.server 8000'
            }
        }
    }
}
