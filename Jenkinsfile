pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'curl -sL https://deb.nodesource.com/setup_18.x | bash -'
                sh 'apt-get install -y nodejs'
                sh 'npm install -g npm'
            }
        }

        stage('Run Unit Tests') {
            steps {
                // Use testing frameworks and scripts to run unit tests
                sh 'npm test'
            }
        }

        stage('Run Build') {
            steps {
                // Build your Node.js application
                sh 'npm build'
                // You can also copy or package your build artifacts here
            }
        }

        // Add more stages for deployment, notifications, etc.
    }

    // Add post-build actions, notifications, etc.
}

