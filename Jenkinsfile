pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh """ssh -t -t $hostname '
                                                                                                                                mkdir $DB_Name tree
                                                                                                                                cd $DB_Name 
                                                                                                                                               
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
    DB_Name = 'asd'
  }
}