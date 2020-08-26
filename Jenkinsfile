pipeline {
  agent any
  stages {
    stage('Validate parameters') {
      when {
        expression {
          params.REQUESTED_ACTION == 'gr'
          [''].contains(params.pass_value)
        }

      }
      steps {
        error "Invalid target environment: ${params.pass_value}"
      }
    }

    stage('other_installation') {
      when {
        expression {
          params.REQUESTED_ACTION == 'gr'
        }

      }
      steps {
        sh """ssh $bbai '
                                                                                                         if [[ -d makula ]]; then echo "directory present"; else mkdir makula;fi                                                                                                                                                                                                     
                                                                                                                                                                                                                                                                                                              
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
    pass = "${params.pass_value}"
    bbai = "${params.Host_name}"
  }
  parameters {
    choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
    string(name: 'Host_name', defaultValue: '', description: '')
    string(name: 'pass_value', defaultValue: '', description: '')
  }
}