pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/kallerdk/devops-lab.git'
            }
        }

        stage('Terraform') {
            steps {
                dir('iac-project/terraform') {
                    sh 'terraform init'
                    sh 'terraform apply -auto-approve'
                }
            }
        }

        stage('Ansible') {
            steps {
                dir('iac-project/ansible') {
                    sh 'ansible-playbook playbook.yml'
                }
            }
        }
    }
}
