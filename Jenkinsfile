pipeline {
    agent any
        docker {
            image 'python:3.9' // Use an official Python Docker image
            args '-u root'     // Optional: run as root if you need to install additional packages
        }
    }

    environment {
        DIRECTORY_PATH = 'https://github.com/ivyztech/Jenkins.git'
        TESTING_ENVIRONMENT = 'staging'
        PRODUCTION_ENVIRONMENT = 'Dominique'
    }

    stages {
        stage('Install Python 3') {
            steps {
                sh '''
                sudo apt-get update
                sudo apt-get install -y python3 python3-venv python3-pip
                '''
            }
        }

        stage('Build') {
            steps {
                echo "fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "compile the code and generate any necessary artefacts"
            }
        }

        stage('Test') {
            steps {
                sh '''
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                python -m unittest discover -s tests
                '''
                echo 'unit tests'
                echo 'integration tests'
            }
        }

        stage('Code Quality Check') {
            steps {
                echo 'check the quality of the code'
            }
        }

        stage('Deploy') {
            steps {
                echo "deploy the application to a testing environment specified by the environment variable: ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Approval') {
            steps {
                script {
                    echo 'Waiting for manual approval...'
                    sleep(time: 10, unit: 'SECONDS')
                    echo 'Approval granted.'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "deploy the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
