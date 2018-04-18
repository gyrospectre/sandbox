pipeline {
  agent any
  stages {
    stage('Bootstrap Hosts') {
      steps {
        ansiblePlaybook(playbook: '/home/billm/site.yml', credentialsId: 'ssh', disableHostKeyChecking: true, inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
      }
    }
  }
}