pipeline {
  agent any
  stages {
    stage('Deploy Confluent') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/kafka.yml', credentialsId: 'ssh', disableHostKeyChecking: true, inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
      }
    }
    stage('Deploy Nifi') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/nifi.yml', credentialsId: 'ssh', inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
      }
    }
    stage('Deploy Elastic') {
      parallel {
        stage('Deploy Elastic') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/elastic.yml', inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root', credentialsId: 'ssh')
          }
        }
        stage('Configure Confluent') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/confluent-setup.yml', credentialsId: 'ssh', inventory: '/home/billm/hosts.yml', sudo: true, sudoUser: 'root')
          }
        }
      }
    }
  }
}