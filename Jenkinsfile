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
                                                                                      cd /script
                                                                                      sed -i "s/pass=.*/pass=$pass/g" sc.sh
                                                                                      ./sc.sh
                                                                                      exit
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
    string(name: 'Host_name', defaultValue: 'None', description: '')
    string(name: 'pass_value', defaultValue: 'None', description: '')
  }
}