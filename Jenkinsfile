pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sshagent(credentials: ['demo']) {
          sh '''ssh -t -t -o StrictHostKeyChecking=no demo@ip-172-31-42-58

'''
        }

      }
    }

  }
  environment {
    first = 'step'
  }
}