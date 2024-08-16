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
                sh '''
                    ls -la
                    node --version
                    npm --version
                    
                    # Install dependencies and update package-lock.json
                    npm install

                    # Perform a clean install using the updated package-lock.json
                    npm ci
                    
                    # Build the project
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
