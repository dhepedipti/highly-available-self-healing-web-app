pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-web-app:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                docker rm -f student-web-container || true

                docker run -d \
                --restart unless-stopped \
                -p 80:80 \
                --name student-web-container \
                student-web-app:latest
                '''
            }
        }

    }
}
