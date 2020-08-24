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
        echo "${env.bbai}"
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
    bbai = input(id: 'userInput', message: 'Likho Kuch',
                         parameters: {String:[
                                        [$class: 'TextParameterDefinition', defaultValue: 'None', description: 'Path of config file', name: 'Config']]})
    }
    parameters {
      choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
    }
  }