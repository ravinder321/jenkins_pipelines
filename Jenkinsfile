pipeline {
  agent any

  environment {
    NETLIFY_AUTH_TOKEN = credentials('nfp_NYrorpn4Fj6pTxGFZUAZtjHvia2i3gdPab17') // Match the ID you set in Jenkins
  }

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

    stage('Deploy to Netlify') {
      steps {
        echo 'Deploying to Netlify...'

        // Install Netlify CLI if not already
        bat 'npm install -g netlify-cli'

        // Deploy to Netlify (adjust site ID or use linked site if already configured)
        bat 'netlify deploy --site=6487e432-9f92-455a-9491-5574eaf195ab --dir=build --auth=%nfp_NYrorpn4Fj6pTxGFZUAZtjHvia2i3gdPab17% --prod'
      }
    }

    stage('Notify') {
      steps {
        echo 'Build, test, and deploy completed!'
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
