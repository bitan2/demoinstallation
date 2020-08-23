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
        sh """ssh $hostname '
        cd /home/bitan/bbai/
        nohup script.sh &
        '
        """
        echo 'abc'
      }
    }

    stage('2nd_one') {
      when {
        expression {
          params.req == 'first'
        }

      }
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