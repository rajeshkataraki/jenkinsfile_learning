pipeline {
  agent any

  environment {
    IZ_USER = credentials('5abd0cab-f9dd-4845-837e-b772151efe20')
    SERVER_CREDENTIALS = credentials('server-credentials')
    VERSION = 1.0.0
  }
  stages {
    
    stage("build") {
      steps {
        echo 'Building the application...'
        echo "Building version ${VERSION}..."
      }
    }
    
    stage("test") {
      when {
        not {
          branch 'master'
        }
      }
      steps {
        echo 'Testing the application...'
      }
    }
    
    stage("deploy") {
      steps {
        echo 'Deploying the application...'
        echo "Deploying with ${SERVER_CREDENTIALS}"
        sh "${SERVER_CREDENTIALS}"
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
