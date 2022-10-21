pipeline {
  environment {
    imagename = "rizvanua/react-app"
  }
  agent any
  stages {
    stage ('Checkout Git Repository') {
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
  }
}
