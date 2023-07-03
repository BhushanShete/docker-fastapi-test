pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Test') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose down'
                sh 'docker-compose up -d'
            }
        }

        stage('Monitoring') {
            steps {
                sh 'docker-compose -f docker-compose-monitoring.yml up -d'
            }
        }
    }

    post {
        always {
            sh 'docker-compose down'
            sh 'docker-compose -f docker-compose-monitoring.yml down'
        }
    }
}
