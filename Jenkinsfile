pipeline {
  agent any
  stages {
    stage('other_installation') {
      steps {
        sh ''' ssh -t -t bitan@172.31.29.115  \'
mkdir download
cd download
mkdir anni
sudo apt install openjdk-8-jdk -y
 \'
        '''
      }
    }

    stage('bolbona') {
      steps {
        echo 'Hello, bitsi!'
      }
    }

  }
}