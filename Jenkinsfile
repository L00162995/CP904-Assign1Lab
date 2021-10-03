pipeline {
  agent any
  tools {
    maven 'apache-maven'
  }
  stages {
    stage('Initialize')
      steps {
        echo 'Initialize Steps'
        sh mvn -version
      }

    stage('Build') {
      steps {
        echo 'maven build'
      }
    }

    stage('Unit Test') {
      steps {
        echo "test successful"'
      }
    }
    stage('Deploy ') {
      parallel {
        stage('Deploy Dev') {
          steps {
            echo 'Deploying in DEV'
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