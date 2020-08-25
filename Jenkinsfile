pipeline {
  agent any
  stages {
    stage('other_installation') {
      when {
        expression {
          params.REQUESTED_ACTION == 'gr'
          params.Host_name != ''
        }

      }
      steps {
        sh """ssh $bbai '
                                      mkdir amar_bbai
                                '
                                 """
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
    bbai = "${params.Host_name}"
  }
  parameters {
    choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
    string(name: 'Host_name', defaultValue: 'None', description: '')
  }
}