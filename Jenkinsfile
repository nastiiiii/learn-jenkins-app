pipeline {
    agent any

    stages {
        stage("Build"){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                echo "Starting build"
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
        stage("Test"){
            steps{
                sh '''
                    echo "Starting test" 
                    test -f "build/imdex.html"
                    npm test
                '''
            }
        }
    }
}