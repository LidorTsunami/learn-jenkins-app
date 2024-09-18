pipeline {
    agent any

    stages {
        stage('Check Docker') {
            steps {
                sh 'docker info'
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm build
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                npm run test
                '''
            }
        }
    }
}