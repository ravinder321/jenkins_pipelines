pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo 'Installing dependencies and building React app...'
        sh 'npm install'
        sh 'npm run build'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'npm test'
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
