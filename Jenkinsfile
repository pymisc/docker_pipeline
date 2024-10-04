pipeline {
  agent { label 'linux' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('unixadm-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'chmod 755 $HOME'
        sh 'docker buildx build .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh "echo Now showing outputs of docker ps, ls -a and ls" 
        sh 'docker ps'
        sh 'docker ls -a'
        sh 'docker ls'
        sh 'docker push unixadm/ubtest:latest'
      }
    }
  }
}
