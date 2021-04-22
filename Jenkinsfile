pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Starting pipeline'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing'
        sh 'npm run test'
      }
    }

    stage('Archive artifact') {
      steps {
        archiveArtifacts(onlyIfSuccessful: true, artifacts: '*.zip')
      }
    }

  }
}