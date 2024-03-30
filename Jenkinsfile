pipeline {
  agent any
  tools {
    nodejs "node"
  }
  stages {
    stage('Install Dependencies'){
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
  }
}