pipeline {
  agent any
  stages {
    stage('other_installation') {
      when {
        expression {
          params.REQUESTED_ACTION == 'gr'
        }

      }
      steps {
        sh ''' ssh -t -t bitan@172.31.29.115  \'
mkdir download
cd download
mkdir anni
sudo apt install openjdk-8-jdk
 \'
        '''
      }
    }

    stage('bolbona') {
      when {
        expression {
          params.REQUESTED_ACTION == 'silence'
        }

      }
      steps {
        echo 'Hello, bitsi!'
      }
    }

  }
  parameters {
    choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
  }
}