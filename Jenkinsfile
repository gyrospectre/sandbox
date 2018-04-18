pipeline {
  agent any
  stages {
    stage('Deploy Kafka Hosts') {
      steps {
        ansiblePlaybook(playbook: '/home/billm/site.yml', credentialsId: 'ssh', disableHostKeyChecking: true, inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
      }
    }
  }
}