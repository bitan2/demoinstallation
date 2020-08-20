pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh 'scp /home/jenkins/script.sh $hostname:/home/bitan/script'
        sh """ssh -t -t $hostname '
                cd script 
                chmod +x script.sh
                ./script.sh
                               
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