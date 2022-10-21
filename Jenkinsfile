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
        sh 'script scripts/build.sh'
      }
    }

    stage('Tests') {
      steps {
        sh 'script scripts/test.sh'
      }
    }

    stage('Image Build') {
      steps {
        script {
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('Push Image') {
      steps {
        script {
          docker.withRegistry('', 'ac99ee09-9b22-4f7f-9aec-a26722bb7b09') {
            docker.image("${registry}:${env.BUILD_ID}").push('latest')
            docker.image("${registry}:${env.BUILD_ID}").push("${env.BUILD_ID}")
          }
        }

      }
    }

  }

  environment {
    registry = 'markony/epam-ci-cd-js-app'
  }
}
