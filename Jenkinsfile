pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                script {
                    checkout scm
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm
                // Install project dependencies
                sh 'yarn'
            }
        }

        stage('Build') {
            steps {
                // Build the React app
                sh 'npm run build'
            }
        }
    }

    post {
        success {
            // Actions to perform after a successful build
            echo 'Build successful! Send notifications, etc.'
        }

        failure {
            // Actions to perform after a failed build
            echo 'Build failed! Send notifications, etc.'
        }
    }
}
