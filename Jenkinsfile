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

    stage('Tests') {
      steps {
        sh '''chmod +x scripts/test.sh
sh scripts/test.sh'''
      }
    }

  }
  environment {
    registry = 'markony/epam-ci-cd-js-app'
  }
}