pipeline {
  agent any
  stages {
    stage('Speak') {
      when {
        expression {
          params.REQUESTED_ACTION == 'gr'
        }

      }
      steps {
        echo 'Hello, bitwiseman!'
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