pipeline {
    agent any

    environment {
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                echo 'Using Maven to compile and package the application.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit...'
                echo 'Running integration tests with Selenium...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis using SonarQube...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency Check...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server at: ${env.STAGING_SERVER}...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging server...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server at: ${env.PRODUCTION_SERVER}...'
            }
        }
    }

    post {
        success {
            mail to: 'dominiquevillafuerte11@gmail.com',
                 subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                 body: "The Jenkins pipeline completed successfully."
        }
        failure {
            mail to: 'dominiquevillafuerte11@gmail.com',
                 subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                 body: "The Jenkins pipeline failed. Check the logs for details."
                attachLog: true 
        }
    }
}
