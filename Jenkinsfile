pipeline {
  agent any
  tools {jdk "java11"}
  stages {
    stage('SCM') {
      steps {
        node('Built-In Node') {
          checkout scm
        }
      }
    }
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'SQScanner'
      }
      steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}