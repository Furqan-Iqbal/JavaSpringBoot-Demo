pipeline {
  agent {
    label 'myDocker' 
  }
  environment {
    Rancher_Jekens_key = credentials('rancher-jekens-key')
  }
  stages {
    stage('Build') {
      steps {
        sh 'Docker build -t registry.hiqs.de/java-web-app:latest .'
      }
    }
    
    stage('Login') {
      steps {
        sh 'echo $registry.hiqs.de | Docker login --username=furqan.iqbal --password=Haiderali@313 registry.hiqs.de'
      }
    }
    stage('Push to Heroku registry') {
      steps {
        sh '''
          Docker tag registry.hiqs.de/java-web-app:latest registry.hiqs.de/$APP_NAME/web
          Docker push registry.hiqs.de/$APP_NAME/web
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
