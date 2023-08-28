pipeline {
    agent any
  
    stages {
        stage("Install Dependencies") {
            agent {
                docker { image 'node:lts-buster-slim' }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                script {
                    // Use testing frameworks and scripts to run unit tests
                    sh 'npm test'
                }
            }
        }

        stage('Run Build') {
            steps {
                script {
                    // Build your Node.js application
                    sh 'npm run build'
                    // You can also copy or package your build artifacts here
                }
            }
        }
  
        // Add more stages for deployment, notifications, etc.
    }

    // Add post-build actions, notifications, etc.
}
