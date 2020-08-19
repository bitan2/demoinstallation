pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh 'ssh -oStrictHostKeyChecking=no demo@ip-172-31-42-58'
      }
    }

  }
  environment {
    first = 'step'
  }
}