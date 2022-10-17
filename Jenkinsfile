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

  }
  environment {
    registry = 'markony/epam-ci-cd-js-app'
  }
}