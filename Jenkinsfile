pipeline {
  agent any
  stages {
    stage('Speak') {
      when {
        expression {
          params.REQUESTED_ACTION == 'greeting'
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
    choice(choices: ['greeting' , 'silence'], description: '', name: 'REQUESTED_ACTION')
  }
}