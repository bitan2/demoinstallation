pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        echo "user is ${env.user}"
        script {
          env.user="bitan"
        }

        sh 'echo build_name=$user'
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