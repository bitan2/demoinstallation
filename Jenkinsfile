pipeline {
  agent any
  stages {
    stage('Validate parameters') {
      steps {
        sh '''IFS=, read -ra values <<< ${params.Host_name}
for v in "${values[@]}"
do
   echo "var is $v"
done'''
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