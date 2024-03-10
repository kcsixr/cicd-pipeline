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
        sh '''echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin docker.io
docker push jenkins_cicd_test_image:$BUILD_NUMBER'''
      }
    }

  }
  environment {
    DOCKERHUB_CREDENTIALS = 'credentials(\'dockerhub-credentials\')'
  }
}