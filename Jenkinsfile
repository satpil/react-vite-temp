pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Copy to /var/www/html') {
            steps {
                // Copy files from Jenkins workspace/dist to /var/www/html/
                sh 'cp -r $WORKSPACE/dist  /var/www/html'

                sh 'sudo chmod 755 /home/ec2-user/html/dist'
            }
        }
    }

    post {
        success {
            echo 'Build successful! Send notifications, etc.'
        }

        failure {
            echo 'Build failed! Send notifications, etc.'
        }
    }
}
