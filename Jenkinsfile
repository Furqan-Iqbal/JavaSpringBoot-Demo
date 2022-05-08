pipeline {
  agent any
  environment {
    Rancher_Jekens_key = credentials('rancher-jekens-key')
  }
  stages {
    stage('Build') {
      steps {
        sh 'Docker build -t registry.hiqs.de/java-web-app1:v1 .'
      }
    }
    
    stage('Login') {
      steps {
        sh 'echo docker login registry.hiqs.de --username=furqan.iqbal --password=Haiderali@3130377956'
      }
    }
    stage('Push to Hiqs registry') {
      steps {
        sh '''
          Docker push registry.hiqs.de/java-web-app1:v1
        '''
      }
    }
  }
}
