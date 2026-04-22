pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ayuhcl/JenkinsPoc.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('Run Conatiner') {
            steps{
                sh 'docker stop my-app || true'
                sh 'docker run my-app || true'
                sh 'docker run -d -p 80:80 --name my-app my-app'

            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
    }
}