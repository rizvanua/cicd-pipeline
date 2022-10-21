pipeline {
  agent {label 'linux'}
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
  }
}
