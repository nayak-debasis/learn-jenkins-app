pipeline {
    agent any

    stages {
        stage('Build') {
            agent any
            environment {
                DOCKER_HOST = 'unix:///home/debasis-nayak/.docker/desktop/docker.sock'
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

        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    
                }
            }
            environment {
                DOCKER_HOST = '/home/debasis-nayak/.docker/desktop/docker.sock'
            }
            steps {
                sh '''
                    test -f build/index.html
                    npm install
                    npm test
                '''
            }
        }
    }
}
