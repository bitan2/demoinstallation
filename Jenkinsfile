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
        sh ''' ssh -t -t bitan@172.31.42.58  \'
mkdir annibitss 
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