pipeline {
   agent any
   stages {
       stage('Clone') {
           steps {
               git 'YOUR_GITHUB_REPO_URL'
           }
       }
       stage('Build Docker Image') {
           steps {
               sh 'docker build -t my-app .'
           }
       }
       stage('Deploy to Docker Server') {
           steps {
               sh '''
               ssh ubuntu@DOCKER_SERVER_IP << EOF
               docker stop my-app || true
               docker rm my-app || true
               docker run -d -p 80:80 --name my-app my-app
               EOF
               '''
           }
       }
   }
}