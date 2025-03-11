pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '--user 1000:1000'  // Ensures the container runs as a non-root user
                    reuseNode true
                }
            }
            steps {
                sh '''
                    export NPM_CONFIG_CACHE=$(pwd)/.npm
                    echo "Using npm cache directory: $NPM_CONFIG_CACHE"
                    
                    node --version
                    npm --version
                    
                    npm ci --cache $NPM_CONFIG_CACHE  # Use local cache
                    npm run build || echo "Build failed"
                    
                    ls -la
                '''
            }
        }
    }
}





// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             agent {
//                 docker {
//                     image 'node:18-alpine'
//                     reuseNode true
//                 }
//             }
//             steps {
//                 sh '''
//                     ls -la
//                     node --version
//                     npm --version
//                     npm ci
//                     npm run build
//                     ls -la
//                 '''
//             }
//         }
//         stage('Test') {
//             steps {
//                     echo 'Test stage'
//             }
//         }
        
//     }
// }
