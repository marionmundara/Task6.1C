pipeline {
    agent any
    environment {
        DIRECTORY_PATH = '/OneDrive/SIT753'
        TESTING_ENVIRONMENT = 'test'
        PRODUCTION_ENVIRONMENT = 'marion' 
    }
    stages {
        stage('Build') {
            steps {
                echo "Building the application using Maven"
                echo "Fetching the source code from ${env.DIRECTORY_PATH}"
                echo "Compiling the code and generate any necessary artifacts."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using JUnit"
                echo "Running integration tests using Selenium"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing the code quality using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP Dependency-Check"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the staging server (e.g., AWS EC2 instance)"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production server (e.g., AWS EC2 instance)"
            }
        }
    }
    post {
        success {
            emailext subject: 'Pipeline Success',
                      body: 'The pipeline has completed successfully',
                      to: 'marionmundara@gmail.com',
                      attachLog: true
        }
        failure {
            emailext subject: 'Pipeline Failure',
                      body: 'The pipeline has failed',
                      to: 'marionmundara@gmail.com',
                      attachLog: true
        }
    }
}
