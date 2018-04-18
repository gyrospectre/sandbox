pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        ws(dir: 'build') {
          readFile 'build.sh'
          pwd()
          writeFile(file: 'build.sh', text: 'woot')
        }

      }
    }
    stage('After') {
      steps {
        readFile 'build.sh'
      }
    }
  }
}