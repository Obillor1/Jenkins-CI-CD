pipeline {
    agent any
        #environment {
            #Build_File_Name = 'laptop.txt'
        #}

    stages {
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
                    npm --version
                    node --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        
    }
}