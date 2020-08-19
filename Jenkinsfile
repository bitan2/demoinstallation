pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh '''sshpass -p demo ssh -t -t demo@ip-172-31-42-58
              mkdir Anni
'''
      }
    }

  }
  environment {
    first = 'step'
  }
}