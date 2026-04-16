pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/sivzz-22/Devops-local.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t devop-local-app .'
            }
        }

        stage('Force Cleanup') {
            steps {
                sh '''
                docker rm -f test_app || true
                docker rm -f test_db || true
                docker-compose down || true
                '''
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Test') {
            steps {
                sh 'docker exec test_app npm test'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}