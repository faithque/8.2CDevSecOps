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
        //bat 'snyk auth' // Authenticate Snyk CLI with the Snyk token
        bat 'npm test || exit /B 0' // For Windows compatibility
        //sh 'npm test || true' // Unix - Allows pipeline to continue despite test failures
      }
    }
    stage('Generate Coverage Report') {
      steps {
        // Ensure coverage report exists
        bat 'npm run coverage || exit /B 0'
        //sh 'npm run coverage || true'
      }
    }
    stage('NPM Audit (Security Scan)') {
      steps {
        bat 'npm audit || exit /B 0'
        //sh 'npm audit || true' // This will show known CVEs in the output
      }
    }
  }
}