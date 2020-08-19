pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh 'pwd'
        sshPut(from: '/var/lib/jenkins/workspace/demoinstallation_master', into: '/home', dryRun: true, remote: 'demo@ip-172-31-42-58')
      }
    }

  }
  environment {
    first = 'step'
  }
}