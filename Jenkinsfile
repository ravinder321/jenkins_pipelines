pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo 'Installing dependencies and building React app...'
        bat 'npm install'
        bat 'npm run build'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        bat 'npm test -- --passWithNoTests'

      }
    }

    stage('Notify') {
      steps {
        echo 'Build and tests completed!'
      }
    }
  }

  post {
    success {
      echo 'Pipeline succeeded 🎉'
    }
    failure {
      echo 'Pipeline failed 💥'
    }
  }
}
