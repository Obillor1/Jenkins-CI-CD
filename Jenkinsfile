pipeline {
    agent any
        environment {
            Build_File_Name = 'laptop.txt'
        }

    stages {
        stage('With Docker') {
            steps {
                sh 'echo With Docker'
            }
        }
        stage('Without Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'echo "Without Docker"'
                sh 'npm --version'
            }
        }
        
    }
}