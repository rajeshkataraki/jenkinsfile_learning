def gv

pipeline {
  agent any

  environment {
    IZ_USER = credentials('5abd0cab-f9dd-4845-837e-b772151efe20')
    //SERVER_CREDENTIALS = credentials('server-credentials')
    VERSION = '1.0.0'
  }

  parameters {
    choice(name: 'MYVERSION', choices: ['1.0.0', '1.2.0', '1.3.0'], description: 'Please choose right version')
    booleanParam(name: 'executeTests', defaultValue: true, description: 'Execute Tests')
  }
  stages {
    
    stage("init") {
      steps {
        script {
          gv = load.script.groovy
        }
      }
    }
    stage("build") {
      steps {
        script {
          gv.buildApp()
        }
        echo 'Building the application...'
        echo "Building version ${VERSION}..."
      }
    }
    
    stage("test") {
      //when {
      //  branch 'master'
      //}
      when {
        expression {
          params.executeTests
        }
      }
      steps {
        script {
          gv.testApp()
        }
       //echo 'Testing the application...'
      }
    }
    
    stage("deploy") {
      steps {
        echo 'Deploying the applicationof version ${params.MYVERSION}'
        echo "Deploying with ${IZ_USER}"
        //sh "ls -l"
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
