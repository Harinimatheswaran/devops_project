pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Checking out the code...'
                checkout scm
            }
        }

        stage('Install') {
            steps {
                echo '📦 Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                script {
                    def status = sh script: 'npm run test', returnStatus: true
                    if (status != 0) {
                        error "❌ Tests failed! Check logs above."
                    }
                }
            }
        }

        stage('Done') {
            steps {
                echo '✅ Build process completed.'
            }
        }
    }
}
