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
                echo 'Building...'
                // If you need to perform build steps, add them here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Copy the index.html to the Apache web server directory
                sh 'cp index.html /var/www/html/'
            }
        }
    }
}
