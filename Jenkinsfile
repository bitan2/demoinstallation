pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh """scp /home/jenkins/script.sh $hostname:/home/bitan/bbai/script.sh """
        sh """ssh -t -t $hostname '
                                                                                                cd bbai 
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