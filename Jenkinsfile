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
        stage('Test'){
            agent any
                steps{
                    sh 'echo "Test stage"'
                    sh 'test -f build/index.html && echo " File exists."  '
                    sh 'npm test'
                }
            
        }
    }
}