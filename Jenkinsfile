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

    stage('2nd_one') {
      steps {
        sh 'echo "valo toh!"'
      }
    }

    stage('3rd_one') {
      when {
        expression {
          params.req == 'second'
        }

      }
      steps {
        echo 'new one'
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