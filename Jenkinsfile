pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh '''ssh -t -t -o StrictHostKeyChecking=no -p "demo" demo@ip-172-31-42-58

'''
      }
    }

  }
  environment {
    first = 'step'
  }
}