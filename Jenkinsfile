pipeline {
  environment {
    imagename = "romeonil/cicd-pipeline-test"
    registryCredential = 'dockerhub'
  }
  agent any
  stages {
    stage('Checkout Git Repository') {
      steps {
        checkout scm
        echo 'scm is chekouted'
      }
    }
    stage('Application Build') {
      steps {
        sh 'script scripts/build.sh'
        echo env.BUILD_ID
      }
    }
    stage('Run tests') {
      steps {
        sh 'script scripts/test.sh'
      }
    }
    stage('Docker Image Build') {
      steps {
        script {
          def dockerImage = docker.build("${imagename}:${env.BUILD_ID}")
        }

      }
    }
    stage('Docker Push Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            def app = docker.image("${registry}:${env.BUILD_ID}")
            app.push('latest')
            app.push("${env.BUILD_NUMBER}")
          }
        }
      }
    }
  }
}

