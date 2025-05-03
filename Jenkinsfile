pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: ' https://github.com/faithque/8.2CDevSecOps.git'
      }
    }
    stage('Install Dependencies') {
      steps {
        //sh 'npm install'
        bat 'npm install' // For Windows compatibility
      }
    }
    stage('Run Tests') {
      steps {
        bat 'npm test || true'
        //sh 'npm test || true' // Allows pipeline to continue despite test failures
      }
    }
    stage('Generate Coverage Report') {
      steps {
        // Ensure coverage report exists
        bat 'npm run coverage || true'
        //sh 'npm run coverage || true'
      }
    }
    stage('NPM Audit (Security Scan)') {
      steps {
        bat 'npm audit || true'
        //sh 'npm audit || true' // This will show known CVEs in the output
      }
    }
  }
}