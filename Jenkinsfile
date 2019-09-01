pipeline {
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
      }
    }
    stage('Push Image') {
      steps {
        script {
          docker.withRegistry( '', registryCredential ) {
            sh 'docker push call900913/basic-nginx:latest'
          }
        }

      }
    }
    stage('Run Container') {
      steps {
        sh 'export PATH=/var/lib/jenkins:$PATH'
        sh 'kubectl apply -f frontend.yml'
      }
    }
  }
  environment {
    registry = 'call900913/basic-nginx'
    registryCredential = 'call900913'
    dockerImage = 'call900913/basic-nginx'
  }
}
