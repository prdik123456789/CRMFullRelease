pipeline {
  agent any
  stages {
    stage('Disable crontab') {
      parallel {
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao01 `hostname`'
          }
        }
        stage('pbcrmao02') {
          steps {
            sh 'ssh pbcrmao02 `hostname`'
          }
        }
        stage('pbcrmao03') {
          steps {
            sh 'ssh pbcrmao03 `hostname`'
          }
        }
        stage('ppcrmao01') {
          steps {
            sh 'ssh ppcrmao01 `hostname`'
          }
        }
        stage('ppcrmao02') {
          steps {
            sh 'ssh ppcrmao02 `hostname`'
          }
        }
        stage('ppcrmao03') {
          steps {
            sh 'ssh ppcrmao03 `hostname`'
          }
        }
        stage('pbcrmin01') {
          steps {
            sh 'ssh pbcrmin01 `hostname`'
          }
        }
        stage('pbcrmin02') {
          steps {
            sh 'ssh pbcrmin02 `hostname`'
          }
        }
        stage('ppcrmin01') {
          steps {
            sh 'ssh ppcrmin01 `hostname`'
          }
        }
        stage('ppcrmin02') {
          steps {
            sh 'ssh ppcrmin02 `hostname`'
          }
        }
        stage('ppcrmcl01') {
          steps {
            sh 'ssh ppcrmcl01 `hostname`'
          }
        }
        stage('pbcrmcl01') {
          steps {
            sh 'ssh pbcrmcl01 `hostname`'
          }
        }
      }
    }
    stage('Disable DB Jobs') {
      steps {
        sh 'stopDB jobs'
      }
    }
    stage('Vystaveni zaslepek') {
      steps {
        bat(script: 'pokus', returnStatus: true)
      }
    }
    stage('Kontrola zaslepky') {
      steps {
        sh 'echo Kontrola zaslepek'
      }
    }
    stage('StopServer - Linux') {
      parallel {
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao02') {
          steps {
            sh 'ssh pbcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao01') {
          steps {
            sh 'ssh ppcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao02') {
          steps {
            sh 'ssh ppcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao03') {
          steps {
            sh 'ssh ppcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmin01') {
          steps {
            sh 'ssh pbcrmin01 `hostname`'
          }
        }
        stage('pbcrmin02') {
          steps {
            sh 'ssh pbcrmin02 `hostname`'
          }
        }
        stage('ppcrmin01') {
          steps {
            sh 'ssh ppcrmin01 `hostname`'
          }
        }
        stage('ppcrmin02') {
          steps {
            sh 'ssh ppcrmin02 `hostname`'
          }
        }
        stage('crmp-s01') {
          steps {
            sh 'ssh crmp-s01 `hostname`'
          }
        }
      }
    }
    stage('Barel - start') {
      steps {
        echo 'Barel - start'
      }
    }
    stage('Stop Legodo Serveru') {
      parallel {
        stage('Stop Legodo Serveru') {
          steps {
            echo 'Stop Legodo Serveru'
          }
        }
        stage('PV1CRMBI1001') {
          steps {
            bat(script: 'stop_legodo.bat', returnStatus: true)
          }
        }
        stage('PV1CRMBI2001') {
          steps {
            bat(script: 'stop_legodo.bat', returnStatus: true)
          }
        }
      }
    }
    stage('Odpojit OSB') {
      parallel {
        stage('pbcrmao01 - OUT') {
          steps {
            sh 'ssh pbcrmao01 echo odpojeni outbound'
          }
        }
        stage('pbcrmao02 - OUT') {
          steps {
            sh 'ssh pbcrmao02 echo odpojeni outbound'
          }
        }
        stage('pbcrmao03 - OUT') {
          steps {
            sh 'ssh pbcrmao03 echo odpojeni outbound'
          }
        }
        stage('ppcrmao01 - OUT') {
          steps {
            sh 'ssh ppcrmao01 echo odpojeni outbound'
          }
        }
        stage('ppcrmao02 - OUT') {
          steps {
            sh 'ssh ppcrmao02 echo odpojeni outbound'
          }
        }
        stage('ppcrmao03 - OUT') {
          steps {
            sh 'ssh ppcrmao03 echo odpojeni outbound'
          }
        }
        stage('pbcrmin01 - IN') {
          steps {
            sh 'ssh pbcrmin01 echo odpojeni inbound'
          }
        }
        stage('pbcrmin02 - IN') {
          steps {
            sh 'ssh pbcrmin02 echo odpojeni inbound'
          }
        }
        stage('ppcrmin01 - IN') {
          steps {
            sh 'ssh ppcrmin01 echo odpojeni inbound'
          }
        }
        stage('ppcrmin02 - IN') {
          steps {
            sh 'ssh ppcrmin02 echo odpojeni inbound'
          }
        }
        stage('ppcrmcl01 - OUT') {
          steps {
            sh 'ssh ppcrmcl01 echo odpojeni outbound'
          }
        }
        stage('pbcrmcl01 - OUT') {
          steps {
            sh 'ssh pbcrmcl01 echo odpojeni outbound'
          }
        }
      }
    }
    stage('Kontrola odchozích front') {
      steps {
        sh 'ssh ppcrmcl01 echo "kontrola odchozich front v DB"'
      }
    }
    stage('Hold Siebel Job C4 Report Scheduller') {
      steps {
        echo 'Hold Siebel Job'
      }
    }
    stage('Kontrola stop Siebel procesu') {
      steps {
        sh 'ssh pbcrmao01 echo kontrola zastaveni siebelu'
      }
    }
    stage('Deploy files') {
      parallel {
        stage('Deploy files') {
          steps {
            echo 'Deploy'
          }
        }
        stage('Admin stuff') {
          steps {
            node(label: 'JH') {
              bat(script: 'deploy_files.bat', returnStatus: true)
            }

          }
        }
        stage('BROWSER SCRIPTS, PUBLIC') {
          steps {
            node(label: 'JH') {
              bat(script: 'deploy_files.bat', returnStatus: true)
            }

          }
        }
        stage('CTL, IFB, UNIX SCRIPTS, SWT') {
          steps {
            node(label: 'JH') {
              bat(script: 'deploy_files.bat', returnStatus: true)
            }

          }
        }
        stage('SRF') {
          steps {
            node(label: 'main') {
              sh 'ssh pbcrmcl01 echo /srv/bin/devc/crm/adm/shell/deploySRF.ksh'
            }
          }
        }     
      }
    }
    stage('StartServer - Linux') {
      parallel {
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao02') {
          steps {
            sh 'ssh pbcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao01') {
          steps {
            sh 'ssh ppcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao02') {
          steps {
            sh 'ssh ppcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao03') {
          steps {
            sh 'ssh ppcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmin01') {
          steps {
            sh 'ssh pbcrmin01 `hostname`'
          }
        }
        stage('pbcrmin02') {
          steps {
            sh 'ssh pbcrmin02 `hostname`'
          }
        }
        stage('ppcrmin01') {
          steps {
            sh 'ssh ppcrmin01 `hostname`'
          }
        }
        stage('ppcrmin02') {
          steps {
            sh 'ssh ppcrmin02 `hostname`'
          }
        }
        stage('crmp-s01') {
          steps {
            sh 'ssh crmp-s01 `hostname`'
          }
        }
      }
    }
    stage('Repository Synchro (FA2)') {
      steps {
        sh 'ssh pbcrmcl01 /srv/bin/${CSAS_ENV}/crm/adm/shell/imp_rep_sync.ksh step2'
      }
    }
    stage('Tasks') {
      steps {
        echo 'Zavolat v Siebelu'
      }
    }
    stage('Workflow Processes') {
      steps {
        echo 'A'
      }
    }
    stage('Migrate Scripts before ADM') {
      steps {
        sh 'ssh ppcrmcl01 echo "spustit w18p_before_ADM_LST_OF_VAL.sql"'
      }
    }
    stage('ADM') {
      steps {
        sh 'ssh ppcrmcl01 echo grep a sed na xml files'
        sh '''ssh ppcrmcl01 echo /srv/bin/${CSAS_ENV}/crm/adm/shell/deployADM.ksh 1-1H4ULZNV
ssh ppcrmcl01 echo /srv/bin/${CSAS_ENV}/crm/adm/shell/deployADM.ksh 1-1H4ULZNX
ssh ppcrmcl01 echo /srv/bin/${CSAS_ENV}/crm/adm/shell/deployADM.ksh 1-1H4UUGQB YES
ssh ppcrmcl01 echo /srv/bin/${CSAS_ENV}/crm/adm/shell/deployADM.ksh 1-1H4UUGQK
ssh ppcrmcl01 echo /srv/bin/${CSAS_ENV}/crm/adm/shell/deployADM.ksh 1-1H4UUGQO'''
      }
    }
    stage('ADM PostDeployment') {
      steps {
        echo 'ADM postdeploy'
      }
    }
    stage('Updating Hosts') {
      steps {
        echo 'Update host on SIebel'
      }
    }
    stage('Import CSOPS') {
      steps {
        echo 'Import CSOPS'
      }
    }
    stage('Check outbound settings') {
      steps {
        sh 'ssh ppcrmcl01 echo check outbound settings wia SQL'
      }
    }
    stage('Genertate Siebel triggers') {
      steps {
        sh 'ssh ppcrmcl01 /srv/bin/${CSAS_ENV}/crm/adm/shell/gentrig.ksh crmp-s01'
      }
    }
    stage('StopServer2 - Linux') {
      parallel {
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao02') {
          steps {
            sh 'ssh pbcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmao01') {
          steps {
            sh 'ssh pbcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao01') {
          steps {
            sh 'ssh ppcrmao01 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao02') {
          steps {
            sh 'ssh ppcrmao02 `echo restart_server.ksh`'
          }
        }
        stage('ppcrmao03') {
          steps {
            sh 'ssh ppcrmao03 `echo restart_server.ksh`'
          }
        }
        stage('pbcrmin01') {
          steps {
            sh 'ssh pbcrmin01 `hostname`'
          }
        }
        stage('pbcrmin02') {
          steps {
            sh 'ssh pbcrmin02 `hostname`'
          }
        }
        stage('ppcrmin01') {
          steps {
            sh 'ssh ppcrmin01 `hostname`'
          }
        }
        stage('ppcrmin02') {
          steps {
            sh 'ssh ppcrmin02 `hostname`'
          }
        }
        stage('crmp-s01') {
          steps {
            sh 'ssh crmp-s01 `hostname`'
          }
        }
      }
    }
    stage('Siebel DB schema') {
      steps {
        echo 'Siebel DB schema'
      }
    }
    stage('Siebel DB Packages') {
      steps {
        echo 'Siebel DB Packages'
      }
    }  
    stage('SIEBSA DB schema') {
      steps {
        echo 'SIEBSA DB schema'
      }
    }
    stage('SIEBSA DB Packages') {
      steps {
        echo 'SIEBSA DB Packages'
      }
    }
    stage('TERMINATOR DB schema') {
      steps {
        echo 'TERMINATOR DB schema'
      }
    }
    stage('TERMINATOR DB Packages') {
      steps {
        echo 'TERMINATOR DB Packages'
      }
    }
    stage('Zmena hesel') {
      steps {
        echo 'Zmena hesel'
      }
    }
  }
}
