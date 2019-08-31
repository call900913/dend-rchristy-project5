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
        sh '''docker image build -t call900913/basic-nginx:latest .

docker push call900913/basic-nginx:latest'''
      }
    }
  }
}