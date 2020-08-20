pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        echo "user is ${env.user}"
        sh 'echo build_nu=$BUILD_NUMBER'
      }
    }

    stage('bolbona') {
      steps {
        sh 'echo "valo toh!"'
      }
    }

  }
  environment {
    host = '172.31.29.115'
    user = 'bitan'
  }
}