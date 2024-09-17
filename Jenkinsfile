pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                ah '''
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
    }
}
