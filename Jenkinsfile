pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t jenkins_cicd_test_image:$BUILD_NUMBER .'
      }
    }

      stage('Push to DockerHub') {
        steps {
          // Push the Docker image to DockerHub
          withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
          sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
          sh 'docker push your-image-name'
                }
            }
        }
  }
 
}
