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
        sh 'scp /home/jenkins/cp.txt demo@172.31.42.58 /manu'
      }
    }

  }
  environment {
    first = 'step'
  }
}