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
        sh 'echo $bbai amar bbai'
      }
    }

    stage('bolbona') {
      when {
        expression {
          params.REQUESTED_ACTION == 'silence'
        }

      }
      steps {
        echo '${env.bbai}'
      }
    }

  }
  environment {
    asd = 'Love'
    bbai = "${params.DB}"
  }
  parameters {
    choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
    string(name: 'DB', defaultValue: 'None', description: '')
  }
}