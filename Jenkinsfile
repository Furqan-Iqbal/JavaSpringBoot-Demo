pipeline {
  agent any
  environment {
    Rancher_Jekens_key = credentials('rancher-jekens-key')
  }
  stages {
    stage('Build') {
      steps {
        sh 'Docker build -t 00313/java-web-app2:latest .'
      }
    }
    
    stage('Login') {
      steps {
        sh 'echo Docker login --username=00313 --password=Haiderali@313'
      }
    }
    stage('Push to Hiqs registry') {
      steps {
        sh '''
         Docker push 00313/java-web-app2:latest
        '''
      }
    }
  }
}
