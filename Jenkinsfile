pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        script {
          checkout scm
        }

      }
    }

    stage('Application Build') {
      steps {
        sh '''chmod +x scripts/build.sh
sh scripts/build.sh'''
      }
    }

  }
  environment {
    registry = 'markony/epam-ci-cd-js-app'
  }
}