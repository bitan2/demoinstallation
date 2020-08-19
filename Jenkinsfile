pipeline {
  agent any
  stages {
    stage('prerequisities') {
      steps {
        sh ''' 
          sshpass -p demo ssh demo@172.31.42.58 \'

mkdir SCPDPRF1
mkdir tmp
mkdir JDAInst
cd JDAInst
mkdir jdafull_inst
cd jdafull_inst
mkdir Weblogic
mkdir P2018_1_SCPO
cd ..
mkdir SCPDPRF1
cd ..
mkdir SCPDPRF1_batch
cd SCPDPRF1_batch
mkdir script
mkdir sql
\' 
 '''
      }
    }

  }
  environment {
    first = 'step'
  }
}