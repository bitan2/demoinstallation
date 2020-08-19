pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        echo 'La LA'
      }
    }

    stage('error') {
      steps {
        sh 'sshpass -p \' demo\' scp /home/jenkins/cp.txt demo@172.31.42.58 /home/demo/manu'
      }
    }

  }
  environment {
    first = 'step'
  }
}