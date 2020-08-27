pipeline {
  agent any
  stages {
    stage('Validate parameters') {
      steps {
        lala()
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