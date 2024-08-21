pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'https://github.com/ivyztech/Jenkins.git'  
        TESTING_ENVIRONMENT = 'staging'
        PRODUCTION_ENVIRONMENT = 'Dominique' 
    }

    stages {
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
