pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh ''' echo "{env.user}"  \'
mkdir download

cd download
mkdir anni
sudo apt install openjdk-11-jre-headless -y
 \'
        '''
      }
    }

    stage('bolbona') {
      steps {
        sh 'echo "valo toh!"'
      }
    }

  }
  environment {
    host = '172.31.29.115'
    user = 'bitan'
  }
}