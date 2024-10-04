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
        sh 'docker build pymisc/docker_pipeline .'
      }
    }
  }
}
