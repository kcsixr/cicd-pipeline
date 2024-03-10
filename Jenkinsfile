pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t jenkins_cicd_test_image:$BUILD_NUMBER .'
      }
    }

    stage('Docker Push') {
      steps {
        sh '''docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD
docker push jenkins_cicd_test_image:$BUILD_NUMBER'''
      }
    }

  }
  environment {
    credentialsId = 'dockerhub-credentials'
    passwordVariable = 'DOCKERHUB_PASSWORD'
    usernameVariable = 'DOCKERHUB_USERNAME'
  }
}