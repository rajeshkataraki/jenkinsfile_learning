pipeline {
  agent any
  
  stages {
    
    stage("build") {
      steps {
        echo 'Building the application...'
      }
    }
    
    stage("test") {
      steps {
        echo 'Testing the application...'
      }
    }
    
    stage("deploy") {
      steps {
        echo 'Deploying the application...'
      }
    }
  }
  post {
    always {
      echo 'I appear always!!!'
    }
    success {
      echo 'I appear only when successful!!!'
    }
    failure {
      echo 'I appear only when failed!!!'
    }
  }
}
