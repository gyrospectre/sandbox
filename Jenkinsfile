pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Test'
        sshPublisher(alwaysPublishFromMaster: true)
      }
    }
  }
}