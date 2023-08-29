pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                sh 'git config user.name "nada-dev"
                sh 'git config user.email "nadaaymanatia@aucegypt.edu"
                checkout scm
            }
        }

    stage  ("Install dependeincies") {
      agent {
        docker {image 'node:18'}
      }
      steps {
        sh 'apt-get update && apt-get install -y git' // Install Git
        sh 'npm install'
      }
    }
        stage('Run Unit Tests') {
            steps {
                script {
                    // Use testing frameworks and scripts to run unit tests
                    //sh 'npm install'
                    sh 'npm test'
                }
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
