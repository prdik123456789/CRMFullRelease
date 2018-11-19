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
      stage('crmp-s01') {
        steps {
          sh 'ssh crmp-s01 `hostname`'
        }
    }
    stage('Barel - start') {
      steps {
        echo 'Barel - start'
      }
    }
  }
}
