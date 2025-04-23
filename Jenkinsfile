pipeline {
    agent any

     environment {
        EC2_HOST = "ubuntu@34.192.76.51"
        DOCKER_TAG = "latest"
        REMOTE_APP_DIR = "/home/ubuntu/app"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository and checkout the latest code
                git branch: 'main', url: 'https://github.com/Likhitha-Konatham/Webpage-Deployment.git'
            }
        }

        stage('Check Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Test SSH to EC2') {
            steps {
                sshagent(['ec2-ssh']) {
                    sh "ssh -o StrictHostKeyChecking=no ${EC2_HOST} 'hostname'"
                }
            }
        }

         stage('Check EC2 Server Version') {
            steps {
                sshagent(['ec2-ssh']) {  
                    sh "ssh -o StrictHostKeyChecking=no ${EC2_HOST} 'cat /etc/os-release'"
                }
            }
        }

        stage('Check Docker Version') {
            steps {
                sshagent(['ec2-ssh']) {
                    sh "ssh -o StrictHostKeyChecking=no ${EC2_HOST} 'docker --version'"
                }
            }
        }

        stage('Copy Files to EC2') {
            steps {
                sshagent(['ec2-ssh']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no ${EC2_HOST} 'mkdir -p ${REMOTE_APP_DIR}'
                        rsync -avz -e "ssh -o StrictHostKeyChecking=no" --exclude='.git' ./ ${EC2_HOST}:${REMOTE_APP_DIR}
                    """
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image with index.html
                    def image = docker.build("webpage:${env.BUILD_ID}", ".")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker container, exposing port 80 for the web server
                    docker.image("webpage:${env.BUILD_ID}").run('-d -p 8094:80')
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete!'
        }
    }
}
