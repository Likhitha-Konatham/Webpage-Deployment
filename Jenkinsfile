pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the latest version of your code
                checkout scm
            }
        }

        stage('Run Web App') {
            steps {
                // Copy the index.html file to a directory where it can be served
                sh 'cp index.html /var/www/html/index.html' // Assuming a local web server like Apache or Nginx is set up
                
                // Restart the web server to reflect changes (Optional, if needed)
                sh 'sudo systemctl restart apache2'  // or 'nginx' for Nginx
            }
        }
    }
}
