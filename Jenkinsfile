pipeline {
  agent any
  stages {
     stage('Build ') {
      steps {
        sh '''chmod +x scripts/build.sh
scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh 'scripts/test.sh'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t kcsixr/jenkins_cicd_test_image:$BUILD_NUMBER .'
      }
    }

    stage('Push to DockerHub') {
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
          sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
          sh 'docker push kcsixr/jenkins_cicd_test_image:$BUILD_NUMBER'
        }

      }
    }

  }
}
