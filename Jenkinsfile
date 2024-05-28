pipeline {
    agent any
    stages {
        stage('Build') { 
            steps { 
                echo "Use a build automation tool- Gradle to compile and package the code."
            }
            
            post {
                success {
                    mail to: "marionmundara@gmail.com",
                    subject: "Build Stage Success",
                    body: "Pipeline Build Stage was successful!",
                    attachmentsPattern: 'logs/build/*.log'
                }
                failure {
                    mail to: 'marionmundara@gmail.com',
                    subject: "Build Stage Failed",
                    body: "Pipeline Build Stage has failed. Please check the attached logs.",
                    attachmentsPattern: 'logs/build/*.log'
                } 
            }
        }

        stage('Unit and Integration Tests') {
            steps { 
                echo " Use test automation tool- Junit for unit tests and integration test purposes."
            }
            post {
                success {
                    mail to: "marionmundara@gmail.com",
                    subject: "Tests Stage Success",
                    body: "Pipeline Test Stage was successful!",
                    attachmentsPattern: 'logs/test/*.log'
                }
                failure {
                    mail to: 'marionmundara@gmail.com',
                    subject: "Tests Stage Failed",
                    body: "Pipeline Test Stage has failed. Please check the attached logs.",
                    attachmentsPattern: 'logs/test/*.log'
                } 
            }
        } 

        stage('Code Analysis') {
            steps { 
                echo " Integrate a code analysis tool- SonarQube."
            }
        }

        stage('Security Scan') {
            steps { 
                echo " Perform a security scan using a tool- OWASP Dependency-Check."
            }
            post {
                success {
                    mail to: "marionmundara@gmail.com",
                    subject: "Security Scan Stage Success",
                    body: "Pipeline Security Scan Stage was successful!",
                    attachmentsPattern: 'logs/security_scan/*.log'
                }
                failure {
                    mail to: 'marionmundara@gmail.com',
                    subject: "Security Scan Stage Failed",
                    body: "Pipeline Security Scan Stage has failed. Please check the attached logs.",
                    attachmentsPattern: 'logs/security_scan/*.log'
                } 
            }
        }
        stage('Deploy to Staging') {
            steps { 
                echo "Deploy the application to a staging server using deployment tool- Docker."
            }
        } 

        stage('Integration Tests on Staging') {
            steps { 
                echo "Run integration tests on the staging environment."
            }
        }

        stage('Deploy to Production') {
            steps { 
                echo " Deploy the application to a production server using deployment tool- Docker."
            }
        }
    }
}
