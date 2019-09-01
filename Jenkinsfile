pipeline {
  environment {
      registry = "call900913/basic-nginx"
      registryCredential = 'call900913'
      dockerImage = ''
  }
  agent any
  stages {
    stage('Lint') {
      steps {
        sh 'tidy -q -e index.html'
      }
    }
    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":latest"
        }
      }
    }
    stage('Push Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
