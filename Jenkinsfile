pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        echo "user is ${env.name007}"
        sh 'echo build_name=$name007'
      }
    }

    stage('bolbona') {
      steps {
        sh 'echo "valo toh!"'
      }
    }

  }
  environment {
    name007 = 'bitan@172.31.29.115'
  }
}