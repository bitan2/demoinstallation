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
    choice(choices: ['gr' , 'silence'], description: '', name: 'REQUESTED_ACTION')
    string(name: 'Host_name', defaultValue: '', description: '')
    string(name: 'pass_value', defaultValue: '', description: '')
  }
}