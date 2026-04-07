pipeline {
   agent any
   stages {
       stage('Clone') {
           steps {
               git 'https://github.com/ayuhcl/JenkinsPoc.git'
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
               ssh -o StrictHostKeyChecking=no  ubuntu@3.238.251.27 << EOF
               docker stop my-app || true
               docker rm my-app || true
               docker run -d -p 80:80 --name my-app my-app
               EOF
               '''
           }
       }
   }
}