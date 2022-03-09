pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS = credentials('tcampest-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t tcampest/dp-alpine-branch1:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push tcampest/dp-alpine-branch1:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
