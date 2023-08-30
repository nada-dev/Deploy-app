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
      stage('SonarQube analysis 1') {
            steps {
                sh 'mvn clean package sonar:sonar'
            }
        }
        stage("Quality Gate 1") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
        stage('SonarQube analysis 2') {
            steps {
                sh 'gradle sonarqube'
            }
        }
        stage("Quality Gate 2") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }

        // Add more stages for deployment, notifications, etc.
    }

    // Add post-build actions, notifications, etc.
}
