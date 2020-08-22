pipeline {
  agent any
  stages {
    stage('other_installation') {
      when {
        expression {
          params.req == 'first'
        }

      }
      steps {
        echo 'eta first'
      }
    }

    stage('bolbona') {
      when {
        expression {
          params.req == 'second'
        }

      }
      steps {
        sh 'echo "valo toh!"'
      }
    }

  }
  environment {
    hostname = 'bitan@172.31.29.115'
    DB_Name = 'asd'
  }
  parameters {
    choice(choices: ['first' , 'second'], description: '', name: 'req')
  }
}