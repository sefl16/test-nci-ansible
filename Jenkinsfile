pipeline {
  agent any
  stages {
    stage('Initialize') {
      parallel {
        stage('Initialize') {
          steps {
            echo 'Hellow world!'
          }
        }
        stage('check python version') {
          steps {
            sh 'python --version'
          }
        }
      }
    }
    stage('Playbooks') {
      parallel {
        stage('Playbooks') {
          steps {
            ansiblePlaybook(playbook: 'playbooks/mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
          }
        }
        stage('ansible version') {
          steps {
            sh 'ansible --version'
          }
        }
      }
    }
    stage('remove_playbook') {
      steps {
        ansiblePlaybook(playbook: 'playbooks/remove_mega_playbook.yaml', colorized: true, inventory: 'inventories/hosts')
      }
    }
  }
}