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
        sh '''sudo docker tag call900913/basic-nginx:latest call900913/basic-nginx:latest
'''
      }
    }
    stage('Push image') {
      steps {
        withDockerRegistry([ credentialsId: "call900913", url: "docker.io" ]) {
          bat "docker push call900913/basic-nginx:latest"
        }
      }
    }
  }
}
