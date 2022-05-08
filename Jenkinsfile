pipeline {
  agent any
  environment {
    Rancher_Jekens_key = credentials('rancher-jekens-key')
  }
  stages {
    stage('Build') {
      steps {
        sh 'Docker build -t 00313/java-web-app:latest .'
      }
    }
    
    stage('Login') {
      steps {
        sh 'echo Docker login --username=00313 --password=Haiderali@313'
      }
    }
    stage('Push to Heroku registry') {
      steps {
        sh '''
          Docker tag 00313/java-web-app:latest 00313/$APP_NAME/web
          Docker push 00313/$APP_NAME/web
        '''
      }
    }
    stage('Release the image') {
      steps {
        sh '''
          heroku container:release web --app=$APP_NAME
        '''
      }
    }
  }
}
