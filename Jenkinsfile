pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'start /B docker-compose up --build'
            }
        }

        stage('Test') {
            steps {
                bat 'start /B docker-compose up --build'
            }
        }

        stage('Deploy') {
            steps {
                bat 'start /B docker-compose down'
                bat 'start /B docker-compose up --build'
            }
        }

        stage('Monitoring') {
            steps {
                bat 'start /B docker-compose -f docker-compose-monitoring.yml up --build'
            }
        }
        post {
        always {
            bat 'start /B docker-compose down'
            bat 'start /B docker-compose -f docker-compose-monitoring.yml down'
            }
        }
        
    }
}
