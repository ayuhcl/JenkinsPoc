pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ayuhcl/JenkinsPoc.git'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
    }
}