pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/var/www/html"
        REPO_URL = "https://github.com/harikamekala222/Car-Application.git"
        BRANCH = "master"
    }

    stages {

        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: "${BRANCH}", url: "${REPO_URL}"
            }
        }

        stage('Verify Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Deploy to nginx') {
            steps {
                sh '''
                echo "Deploying website to nginx directory..."
                sudo rm -rf ${DEPLOY_DIR}/*
                sudo cp -r * ${DEPLOY_DIR}/
                '''
            }
        }

        stage('Restart nginx') {
            steps {
                sh 'sudo systemctl restart nginx'
            }
        }
    }

    post {
        success {
            echo "Deployment Successful!"
        }
        failure {
            echo "Deployment Failed!"
        }
    }
}
