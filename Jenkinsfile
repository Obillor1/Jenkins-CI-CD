pipeline {
    agent any

    environment {
        NODE_OPTIONS = "--openssl-legacy-provider"
        NPM_CONFIG_CACHE = "/var/lib/jenkins/.npm"
    }

    stages {
        stage('Prepare Environment') {
            steps {
                sh '''
                    sudo chown -R $(id -u):$(id -g) /var/lib/jenkins/.npm || true
                '''
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    rm -rf node_modules package-lock.json
                    npm install typescript@4.9.5 --save-dev
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test stage'
            }
        }
    }
}
