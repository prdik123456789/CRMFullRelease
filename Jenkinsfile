pipeline {
  agent any
  stages {
    stage('Disable crontab') {
      parallel {
        stage('Disable crontab') {
          steps {
            sh 'ssh dpcrmvc31 crontab -l > ~/remote/stage/bkp_cron_`whoami`_`hostname`_$(date +%Y%m%d)'
          }
        }
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
        stage('pbcrmao01') {
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
      }
    }
    stage('Disable DB Jobs') {
      steps {
        sh 'stopDB jobs'
      }
    }
    stage('StopServer - Linux') {
      steps {
        sh 'ssh server stop server'
      }
    }
  }
}