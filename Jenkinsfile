pipeline {
  agent any
  stages {
    stage('Disable CrontabJobs') {
      parallel {
        stage('Disable CrontabJobs') {
          steps {
            sh 'ssh dpcrmvc31 crontab -l > ~/remote/stage/bkp_cron_`whoami`_`hostname`_$(date +%Y%m%d)'
          }
        }
        stage('') {
          steps {
            sh 'ssh dpcrmvc31 crontab -l > ~/remote/stage/bkp_cron_`whoami`_`hostname`_$(date +%Y%m%d)'
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