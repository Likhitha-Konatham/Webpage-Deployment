pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository
                script {
                    // Use a more robust way to clone the repository and specify the branch
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/main']],  // Change 'main' if your branch is different
                        userRemoteConfigs: [[url: 'https://github.com/d-Sujeeth/Jenkins-Pipeline']]
                    ])
                }
            }
        }

        stage('Run HTML Code') {
            steps {
                // Start a simple HTTP server to run HTML code
                script {
                    // Ensure Python is available and run the HTTP server
                    sh '''
                        if command -v python3 &>/dev/null; then
                            python3 -m http.server 8000
                        elif command -v python &>/dev/null; then
                            python -m http.server 8000
                        else
                            echo "Python is not installed"
                            exit 1
                        fi
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
