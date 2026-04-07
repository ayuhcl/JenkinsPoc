pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t jenkinspoc .
                '''
            }
        }

        stage('Deploy to Apache Server') {
            steps {
                sh '''
                ssh ubuntu@3.234.210.9 << EOF
                  docker stop jenkinspoc || true
                  docker rm jenkinspoc || true
                  docker run -d --name jenkinspoc jenkinspoc
                EOF
                '''
            }
        }
    }
}
