pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        build '1 RunDevelopmentProjectBuild'
      }
    }

    stage('Tx_Api') {
      parallel {
        stage('Tx_Api') {
          steps {
            build 'RunAutomationTests_API'
          }
        }

        stage('Tx_Web') {
          steps {
            build 'RunAutomationTests_Web'
          }
        }

        stage('Tx_Mobile') {
          steps {
            build 'RunAutomationTests_Mobile'
          }
        }

        stage('Performance ') {
          steps {
            build 'Performance_Tests'
          }
        }

      }
    }

    stage('SonarQube') {
      steps {
        build 'RunAutomationTests_SonarQube'
      }
    }

  }
}