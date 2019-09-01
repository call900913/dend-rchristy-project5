pipeline {
  environment {
      registry = "call900913/basic-nginx"
      registryCredential = 'call900913'
      dockerImage = "call900913/basic-nginx"
  }
  agent any
  stages {
    stage('Lint') {
      steps {
        sh 'tidy -q -e index.html'
      }
    }
    stage('Build Image') {
      steps {
        sh 'sudo docker image build -t call900913/basic-nginx:latest .'
        sh '''sudo docker tag call900913/basic-nginx:latest call900913/basic-nginx:latest
'''
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
