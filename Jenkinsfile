pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch:'main',
                url: 'https://github.com/ayuhcl/JenkinsPoc.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-ci-cd-image:latest .'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook -i ansible/inventory ansible/deploy.yml'
            }
        }
    }
}