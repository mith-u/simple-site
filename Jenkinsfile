pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/mith-u/simple-site.git'
            }
        }
        stage('Build & Deploy') {
            steps {
                sh '''
                docker stop devops-site || true
                docker rm devops-site || true
                docker build -t devops-site .
                docker run -d -p 8081:80 --name devops-site devops-site
                '''
            }
        }
    }
}

