pipeline {
  agent any
  stages {
    stage('Deploy Kafka') {
      steps {
        ansiblePlaybook(playbook: 'site.yml', credentialsId: 'ssh', disableHostKeyChecking: true, inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
      }
    }
    stage('Deploy Nifi') {
      steps {
        ansiblePlaybook(playbook: 'nifi.yml', credentialsId: 'ssh', inventory: '/home/billm/hosts.yml')
      }
    }
  }
}