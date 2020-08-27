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

  }
  environment {
    bbai = "${params.Host_name}"
  }
  parameters {
    string(name: 'Host_name', defaultValue: '', description: '')
  }
}