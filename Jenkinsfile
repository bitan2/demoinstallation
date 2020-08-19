pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh 'pwd'
        sshPut(from: '/var/lib/jenkins/workspace/demoinstallation_master', into: 'demo@ip-172-31-42-58', dryRun: true)
      }
    }

  }
  environment {
    first = 'step'
  }
}