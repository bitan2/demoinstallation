pipeline {
  agent any
  stages {
    stage('Create_Directories_structure') {
      when {
        expression {
          params.req == 'before_root_app_execution'
        }

      }
      steps {
        sh 'rsync -avz $WORKSPACE/automation_script $App_hostname:.'
        sh """ssh -t -t $App_hostname '
                          mkdir /manu
                          cd /manu
                          mkdir $DB_name tmp JDAInst $DB_name_batch oracle
                          cd JDAInst 
                          mkdir jdafull_inst $DB_name
                          cd jdafull_inst
                          mkdir Weblogic P2018_1_SCPO P2018_1_SCPO_sre P2018_1_Platform P2018_1_Platform_sre
                          cd ../../
                          cd $DB_name_batch
                          mkdir script sql xml log export parm archive_log fix
                       '
                       """
      }
    }

    stage('Copy_Package_file_to_Host_untar') {
      when {
        expression {
          params.req == 'before_root_app_execution'
        }

      }
      environment {
        package_path_jenkins = '/home/jenkins/[]'
        jdafull_inst_path = '/manu/JDAInst/jdafull_inst'
      }
      steps {
        sh 'scp ${env.package_path_jenkins}/scpoweb-2018.1.0.16-aix.tar ${env.App_hostname}:${env.jdafull_inst_path}/P2018_1_SCPO'
        sh 'scp ${env.package_path_jenkins}/jdaplatform-2018.1.0.17-aix.tar ${env.App_hostname}:${env.jdafull_inst_path}/P2018_1_Platform'
        sh 'scp ${env.package_path_jenkins}/weblogic12213_64bit.zip ${env.App_hostname}:${env.jdafull_inst_path}/Weblogic'
        sh 'scp ${env.package_path_jenkins}/aixppc64_12201_client.zip ${env.App_hostname}:/manu/Oracle'
        sh """ ssh -t -t $App_hostname '
                        cd $jdafull_inst_path/P2018_1_Platform
                        tar -xvf jdaplatform-2018.1.0.17-aix.tar
                        cp -p installPlatform.properties installPlatform.properties.orig
                        cp installPlatform.properties /manu/JDAInst/$DB_name
                        cd $jdafull_inst_path/P2018_1_SCPO
                        tar -xvf scpoweb-2018.1.0.16-aix.tar
                        '
                        """
      }
    }

    stage('work_with_Platform_property_file') {
      when {
        expression {
          params.req == 'before_root_app_execution'
        }

      }
      steps {
        sh """ ssh -t -t $App_hostname '
                       cp -p installPlatform.properties installPlatform_admin.properties
                       cp -p installPlatform.properties installPlatform_webworks1.properties
                       cp -p installPlatform.properties installPlatform_webworks2.properties
                       cp -p installPlatform.properties installPlatform_webworks3.properties
                       cd $script_path
                       chmod +x admin_properties.sh
                       chmod +x webworks1_properties.sh
                       chmod +x webworks2_properties.sh
                       chmod +x webworks3_properties.sh
                       ./admin_properties.sh
                       ./webworks1_properties.sh
                       ./webworks2_properties.sh
                       ./webworks3_properties.sh
                       '
                       """
      }
    }

    stage('work_with_SCPO_property_file') {
      when {
        expression {
          params.req == 'before_root_app_execution'
        }

      }
      steps {
        sh """ssh -t -t $App_hostname '
                       cp -p installPlatform_admin.properties /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                       cp -p installPlatform_webworks1.properties /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                       cp -p installPlatform_webworks2.properties /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                       cp -p installPlatform_webworks3.properties /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                       cd $script_path
                       chmod +x installSCPOWeb_admin.properties
                       chmod +x installSCPOWeb_webworks1_properties.sh
                       chmod +x installSCPOWeb_webworks2_properties.sh
                       chmod +x installSCPOWeb_webworks3_properties.sh
                       ./installSCPOWeb_admin_properties.sh
                       ./installSCPOWeb_webworks1_properties.sh
                       ./installSCPOWeb_webworks2_properties.sh
                       ./installSCPOWeb_webworks3_properties.sh
                       cd /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                       chmod +x installPlatform.bin
                       cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb
                       cp -p installSCPOWeb.properties installSCPOWeb.properties.orig
                       cp installSCPOWeb.properties /manu/JDAInst/$DB_name
                       cp -p installSCPOWeb_admin.properties /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                       cp -p installSCPOWeb_webworks1.properties /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                       cp -p installSCPOWeb_webworks2.properties /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                       cp -p installSCPOWeb_webworks3.properties /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                       cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                       chmod +x installSCPOWeb.bin
                       cd /manu/oracle
                       unzip aixppc64_12201_client.zip
                       mkdir base
                       chmod 775 base
                       cd /manu/oracle/client/response
                       cp client_install.rsp client_install.rsp.orig
                       cd /manu/oracle/client
                       ./runInstaller -responseFile /manu/oracle/client/response/client_install.rsp -printdiskusage -printmemory -printtime -silent -waitforcompletion -noconfig
                    '
                    """
      }
    }

    stage('installation') {
      when {
        expression {
          params.req == 'after_root_app_execution'
        }

      }
      steps {
        sh """ssh -t -t $App_hostname '
                          cd /manu/oracle/base/client/cfgtoollogs
                          configToolAllCommands RESPONSE_FILE=/manu/oracle/client/response/client_install.rsp
                          sqlplus stsc/***@$DB_name
                          exit
                          tnsping $DB_name
                          cd /manu/JDAInst/jdafull_inst/Weblogic
                          java -jar fmw_12.2.1.3.0_wls.jar -silent -responseFile /manu/JDAInst/jdafull_inst/Weblogic/weblogic_2018_modified.rsp -invPtrLoc /manu/JDAInst/jdafull_inst/Weblogic/oraInst.loc
                          cd /manu/JDAInst/jdafull_inst/P2018_1_Platform/jdaplatform/platform/aix
                          export IATEMPDIR=/manu/tmp
                          nohup installPlatform.bin -f installPlatform_admin.properties > installproperties_admin_perf1_app1.out &
                          nohup installPlatform.bin -f installPlatform_webworks1.properties > installproperties_webworks1_perf1_app1.out &
                          nohup installPlatform.bin -f installPlatform_webworks2.properties > installproperties_webworks2_perf1_app1.out &
                          nohup installPlatform.bin -f installPlatform_webworks3.properties > installproperties_webworks3_perf1_app1.out &
                          cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                          export IATEMPDIR=/manu/tmp
                          nohup installSCPOWeb.bin -f installSCPOWeb_admin.properties >$DB_name_2018_SCPO_admin_App1.out &
                          nohup installSCPOWeb.bin -f installSCPOWeb_webworks1.properties >$DB_name_2018_SCPO_webwork1_App1.out & 
                          nohup installSCPOWeb.bin -f installSCPOWeb_webworks2.properties >$DB_name_2018_SCPO_webwork2_App1.out &
                          nohup installSCPOWeb.bin -f installSCPOWeb_webworks3.properties >$DB_name_2018_SCPO_webwork3_App1.out &
                          '
                          """
      }
    }

    stage('SRE_Installation_before_root') {
      when {
        expression {
          params.req == 'before_root_sre_execution'
        }

      }
      environment {
        package_path_jenkins = '/home/jenkins/'
        jdafull_inst_path = '/manu/JDAInst/jdafull_inst'
      }
      steps {
        sh 'rsync -avz $WORKSPACE/automation_script $SRE_hostname:.'
        sh """ssh -t -t $SRE_hostname '
                          mkdir /manu
                          cd /manu
                          mkdir $DB_name tmp JDAInst $DB_name_batch oracle
                          cd JDAInst 
                          mkdir jdafull_inst $DB_name
                          cd jdafull_inst
                          mkdir Weblogic P2018_1_SCPO P2018_1_SCPO_sre P2018_1_Platform P2018_1_Platform_sre
                          cd ../../
                          cd $DB_name_batch
                          mkdir script sql xml log export parm archive_log fix
                          '
                          """
        sh 'scp ${env.package_path_jenkins}/scpoweb-2018.1.0.16-aix.tar ${env.SRE_hostname}:${env.jdafull_inst_path}/P2018_1_SCPO_sre'
        sh 'scp ${env.package_path_jenkins}/jdaplatform-2018.1.0.17-aix.tar ${env.SRE_hostname}:${env.jdafull_inst_path}/P2018_1_Platform_sre'
        sh 'scp ${env.package_path_jenkins}/aixppc64_12201_client.zip ${env.SRE_hostname}:/manu/oracle'
        sh """ ssh -t -t $SRE_hostname '
                          cd /manu/JDAInst/jdafull_inst/P2018_1_Platform_sre
                          gunzip jdaplatform-2018.1.0.17-aix.tar.gz
                          tar -xvf jdaplatform-2018.1.0.17-aix.tar
                          cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO_sre
                          gunzip scpowebsre-2018.1.0.18-aix.tar.gz
                          tar -xvf scpowebsre-2018.1.0.18-aix.tar
                          cd /manu/JDAInst/jdafull_inst/P2018_1_Platform_SRE/jdaplatform
                          cp -p installPlatform_SRE.properties installPlatform_SRE.properties.orig
                          cp installPlatform_SRE.properties /manu/JDAInst/SCPDPRF1

                          cd $script_path
                          chmod +x installPlatform_SRE_properties.sh
                          ./installPlatform_SRE_properties.sh

                          cd /manu/JDAInst/SCPDPRF1
                          cp -p installPlatform_SRE.properties /manu/JDAInst/jdafull_inst/P2018_1_Platform_sre /jdaplatform/platform_sre/aix
                          cd /manu/JDAInst/jdafull_inst/P2018_1_Platform_sre/jdaplatform/platform_sre/aix
                          chmod +x installPlatform_SRE.bin
                          cd /manu/JDAInst/jdafull_inst/ P2018_1_SCPO_sre/scpoweb_sre
                          cp -p installSCPOWeb_SRE.properties installSCPOWeb_SRE.properties.orig
                          cp installSCPOWeb_SRE.properties /manu/JDAInst/SCPDPRF1
                          
                          cd $script_path
                          chmod +x installSCPOWeb_SRE_properties.sh
                          ./installSCPOWeb_SRE_properties.sh

                          cp -p installSCPOWeb_SRE.properties /manu/JDAInst/jdafull_inst/P2018_1_SCPO_sre/scpoweb_sre/aix
                          cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO/scpoweb/aix
                          
                          chmod +x installSCPOWeb_SRE.bin
                          cd /manu/oracle
                          unzip aixppc64_12201_client.zip
                          mkdir base
                          chmod 775 base
                          cd /manu/oracle/client/response
                          cp client_install.rsp client_install.rsp.orig
                          cd /manu/oracle/client
                          ./runInstaller -responseFile /manu/oracle/client/response/client_install.rsp -printdiskusage -printmemory -printtime -silent -waitforcompletion -noconfig
                          '
                          """
      }
    }

    stage('after_root_sre_execution') {
      when {
        expression {
          params.req == 'after_root_sre_execution'
        }

      }
      steps {
        sh """ ssh $SRE_hostname '
                        cd /manu/oracle/client
                        runInstaller -executeConfigTools -responseFile /manu/oracle/client/response/client_install.rsp -silent
                        sqlplus stsc@SCPDPRF1
                        tnsping SCPDPRF1 
                        cd /manu/JDAInst/jdafull_inst/P2018_1_Platform_SRE/jdaplatform/platform_sre/aix
                        export IATEMPDIR=/manu/tmp
                        nohup installPlatform_SRE.bin -f installPlatform_SRE.properties >install_platform_sre1_exec1.log &
                        cd /manu/JDAInst/jdafull_inst/P2018_1_SCPO_sre/scpoweb_sre/aix
                        export IATEMPDIR=/manu/tmp
                        nohup installSCPOWeb_SRE.bin -f installSCPOWeb_SRE.properties >install_scpoweb_sre1_exec2.log &
                        cd /manu/SCPDPRF1/sre/config/bin/platform
                        cp startNodePoolManager startNodePoolManager_ddmon 
                        '
                        """
      }
    }

  }
  environment {
    App_hostname = 'bitan@[server_name]'
    SRE_hostname = 'bitan@[server_name]'
    DB_name = 'SCPDPRF1'
    script_path = ''
  }
  parameters {
    choice(choices: ['before_root_app_execution' , 'after_root_app_execution' , 'before_root_sre_execution' , 'after_root_sre_execution'], description: '', name: 'req')
  }
}