pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }

        stage('Run Build') {
            steps {
                sh 'npm run build'
            }
        }

        // Add more stages for deployment, notifications, etc.
    }

    // Add post-build actions, notifications, etc.
}
