pipeline {
  agent any
  stages {
    stage('Disable CrontabJobs') {
      steps {
        sh 'ssh dpcrmvc31 crontab -l > ~/remote/stage/bkp_cron_`whoami`_`hostname`_$(date +%Y%m%d)'
      }
    }
  }
}