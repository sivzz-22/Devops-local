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
                sh 'docker compose build'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Test') {
            steps {
                sh 'docker exec test_app npm test'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker compose down'
            }
        }
    }
}