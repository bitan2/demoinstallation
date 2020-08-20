pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh ' echo "{env.user}"'
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