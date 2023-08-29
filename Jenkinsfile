pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

    stage  ("Install dependeincies") {
      agent {
        docker {image 'node:18'}
      }
      steps {
        sh 'npm install'
      }
    }
        stage('Run Unit Tests') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                sh 'npm test'
            }
        }

        stage('Run Build') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                
                sh 'npm run build'
            }
        }

        // Add more stages for deployment, notifications, etc.
    }

    // Add post-build actions, notifications, etc.
}
