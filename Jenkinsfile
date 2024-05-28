pipeline {
    agent any

    environment {
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
        RECIPIENTS = 'marionmundara@gmail.com'
        // Add more variables as required
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Use your chosen tool to build your code, e.g., Maven, Gradle
                sh 'mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests...'
                // Run your tests e.g., with Maven Surefire for unit tests
                sh 'mvn test'
            }
            post {
                always {
                    // Assuming JUnit plugin is being used
                    junit 'target/surefire-reports/*.xml'
                    // If the test stage fails, send an email 
                    script {
                        if (currentBuild.currentResult == 'FAILURE') {
                            mail to: "${RECIPIENTS}",
                                 subject: "Failed Unit and Integration Tests",
                                 body: "The unit and integration tests have failed. Please check the logs for further details."
                        }
                    }
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                // Use a code quality tool like SonarQube, integrate with Jenkins
                sh 'sonar-scanner'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Use a security analysis tool like OWASP ZAP, integrate with Jenkins
                sh 'zap-cli scan --target http://your-app-url'
            }
            post {
                always {
                    // Send email after security scan
                    mail to: "${RECIPIENTS}",
                         subject: "Security Scan Completed",
                         body: "The security scan has been completed. Please check the reports for further details."
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Example: use a script to deploy to staging server
                sh './deploy-staging.sh ${STAGING_SERVER}'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Similar to integration tests before staging
                sh 'mvn verify -Pintegration-tests'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Example: use a script to deploy to production server
                sh './deploy-production.sh ${PRODUCTION_SERVER}'
            }
        }
    }
    
    post {
        failure {
            mail to: "${RECIPIENTS}",
                 subject: "Pipeline Failed",
                 body: "The pipeline execution has failed. Please check Jenkins for details."
        }
    }
}
