pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        sh 'git branch: \'main\', url: \'https://github.com/kcsixr/cicd-pipeline.git\''
      }
    }

    stage('Build') {
      steps {
        sh '''chmod +x scripts/build.sh
scripts/build.sh'''
      }
    }

  }
}