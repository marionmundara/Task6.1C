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
                
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests...'
                // Run your tests e.g., with Maven Surefire for unit tests
            
            }
            post {
                always {
                    // Assuming JUnit plugin is being used
                    junit 'target/surefire-reports/*.xml'
                    // If the test stage fails, send an email 
                    script {
                        def log = manager.build.logFile.text
                        def recipient = 'marionmars99@gmail.com'
                        def subject = "Stage ${env.STAGE_NAME} Completed"
                        def body = "The stage ${env.STAGE_NAME} has completed. Please find the log attached."

            // Use the Email Ext plugin to send an email with an attachment
            emailext (
                to: recipient,
                subject: subject,
                body: body,
                attachLog: true // To attach the log
            )
                        }
                    }
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                // Use a code quality tool like SonarQube, integrate with Jenkins
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Use a security analysis tool like OWASP ZAP, integrate with Jenkins
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
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Similar to integration tests before staging
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Example: use a script to deploy to production server
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
