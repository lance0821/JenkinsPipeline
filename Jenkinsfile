pipeline {
  agent any
  tools {
    nodejs "node"
  }
  environment {
    imageName = 'lance0821/react-app'
    registryCredential = 'dockerhub-creds'
    dockerImage = ''
  }
  stages {
    stage('Install Dependencies'){
      steps {
        sh 'npm install'
      }
    }
    stage('Tests') {
      steps {
        sh 'npm test'
      }
    }
    stage('Building Image') {
      steps {
        script {
          dockerImage = docker.build imageName
        }
      }
    }
        stage('Deploy Image') {
      steps {
        script {
          // Assuming registryCredential is the correct ID for Docker Hub credentials
          docker.withRegistry('https://registry.hub.docker.com', registryCredential) {
            dockerImage.push("${env.BUILD_NUMBER}")
          }
        }
      }
    }
  }
}