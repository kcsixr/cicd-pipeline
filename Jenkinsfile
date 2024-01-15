pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x scripts/build.sh
scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x scripts/build.sh
scripts/build.sh'''
      }
    }

    stage('Build a docker image') {
      steps {
        sh 'docker build -t jenkins_cicd_test_image:$BUILD_NUMBER .'
      }
    }

  }
}