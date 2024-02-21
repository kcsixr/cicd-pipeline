pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''chmod +x ./scripts/build.sh
./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t jenkins_cicd_test_image:$BUILD_NUMBER .'
      }
    }

  }
}