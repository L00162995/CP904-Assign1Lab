pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        build 'sh hostname '
      }
    }

    stage('Deploy ') {
      parallel {
        stage('Deploy Dev') {
          steps {
            echo 'Deploying in DEV with test'
          }
        }

        stage('Deploy PREPROD') {
          steps {
            echo 'Deploying in PREPROD'
          }
        }

        stage('DeployPROD') {
          steps {
            echo 'Deploying in PROD'
          }
        }

      }
    }

    stage('Test') {
      steps {
        sh 'sh echo "test successful"'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts(allowEmptyArchive: true, artifacts: 'dev-preprod-prod')
      }
    }

  }
  environment {
    test = 'cat file'
    test2 = 'cat file2'
  }
}