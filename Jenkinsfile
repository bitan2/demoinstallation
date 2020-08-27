pipeline {
  agent any
  stages {
    stage('Validate parameters') {
      steps {
        echo 'valo'
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