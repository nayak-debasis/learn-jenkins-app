pipeline {
    agent any

    stages {
        stage('Build') {
             agent any
                 environment {
                    DOCKER_HOST = 'unix:///home/debasis-nayak/.docker/desktop/docker.sock'
                        }
        stage('Test'){
            agent any
            sh ' echo "Test stage"'
        }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}