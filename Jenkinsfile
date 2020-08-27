pipeline {
  agent any
  stages {
    stage('Validate parameters') {
      steps {
        script {
          def art = ${params.Host_name}.split(';')
          for (a in art) {
            echo a

          }
        }

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
    string(name: 'Host_name', defaultValue: '', description: '')
  }
}