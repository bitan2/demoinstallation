pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh """ssh -t -t $hostname '
               mkdir bbai 
             '
             """
      }
    }

    stage('bolbona') {
      steps {
        sh 'echo "valo toh!"'
      }
    }

  }
  environment {
    hostname = 'bitan@172.31.29.115'
  }
}