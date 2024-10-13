pipeline {
    agent any

    environment {
        NODE_VERSION = '16.x' // Using Node.js version 16.x
    }

    stages {
        stage('Checkout') {
            steps {
                // Fetch code from your GitHub repository
                git branch: 'main', url: 'https://github.com/ashutosh-gitdev/nodejs-app.git'
            }
        }

        stage('Install Node.js') {
            steps {
                script {
                    // Install Node.js on the Jenkins agent
                    sh 'curl -sL https://deb.nodesource.com/setup_16.x | bash -'
                    sh 'apt-get install -y nodejs'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install project dependencies using npm
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests
                sh 'npm test' // Assumes you have test scripts in package.json
            }
        }

        stage('Build') {
            steps {
                // Build the project, assuming there is a build script
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Simulate deploying the app
                echo 'Deploying application to production server...'
                // Fake deployment command (modify based on your actual deployment)
                sh 'ssh user@123.45.67.89 "cd /var/www/nodejs-app && git pull origin main && npm install && pm2 restart app"'
            }
        }
    }

    post {
        always {
            // Cleanup or notifications, e.g., send notifications or archive artifacts
            echo 'Pipeline completed!'
        }
        success {
            echo 'Build and deployment succeeded!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}
