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
        sh 'sshpass -p ${pass} scp /home/jenkins/cp/cp.txt demo@172.31.42.58:/home/demo/'
      }
    }

  }
  environment {
    first = 'step'
  }
}