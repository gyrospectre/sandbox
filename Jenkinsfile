pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Test'
        ansiblePlaybook 'runbuild'
      }
    }
  }
}