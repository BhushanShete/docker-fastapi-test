pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'start /B docker-compose build'
            }
        }

        stage('Test') {
            steps {
                bat 'start /B docker-compose up -d'
            }
        }

        stage('Deploy') {
            steps {
                bat 'start /B docker-compose down'
                bat 'start /B docker-compose up -d'
            }
        }

        stage('Monitoring') {
            steps {
                bat 'start /B docker-compose -f docker-compose-monitoring.yml up -d'
            }
        }
    }

    post {
        always {
            bat 'start /B docker-compose down'
            bat 'start /B docker-compose -f docker-compose-monitoring.yml down'
        }
    }
}
