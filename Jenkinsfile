pipeline {
    agent {
        docker {
            image 'python:3.9'
            args '-u root'
        }
    }

    stages {
        stage('Test Docker and Python') {
            steps {
                sh '''
                python --version
                pip --version
                '''
            }
        }
    }
}
