pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/harikamekala222/Car-Application.git'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                cp -r * /var/www/html/
                '''
            }
        }

    }
}
