pipeline {
  agent any
  stages {
    stage('Deploy Confluent') {
      parallel {
        stage('Deploy Confluent') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/kafka.yml', credentialsId: 'ubuntu', disableHostKeyChecking: true, inventory: '/home/user/hosts.yml', become: true, becomeUser: 'root')
          }
        }
        stage('Deploy Nifi') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/nifi.yml', credentialsId: 'ssh', sudo: true, sudoUser: 'root')
          }
        }
      }
    }
    stage('Deploy Elastic') {
      parallel {
        stage('Deploy Elastic') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/elastic.yml', inventory: '/home/user/hosts.yml', sudo: true, sudoUser: 'root', credentialsId: 'ssh')
          }
        }
        stage('Configure Confluent') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/confluent-setup.yml', credentialsId: 'ssh', inventory: '/home/user/hosts.yml', sudo: true, sudoUser: 'root')
          }
        }
      }
    }
    stage('Deploy Kibana') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/kibana.yml', inventory: '/home/user/hosts.yml', sudo: true, sudoUser: 'root', credentialsId: 'ssh')
      }
    }
  }
}