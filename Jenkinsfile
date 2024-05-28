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
                    subject: "Build Stage - Status: Success",
                    body: "Pipeline Success in Build Stage!",
                    attachments: "${manager.build.logFile}"
                }
                failure {
                    mail to: "marionmundara@gmail.com",
                    subject: "Build Stage - Status: Failure",
                    body: "Pipeline Failed in Build Stage!",
                    attachments: "${manager.build.logFile}"
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
                    subject: "Test Stage - Status: Success",
                    body: "Pipeline Success in Test Stage!",
                    attachments: "${manager.build.logFile}"
                }
                failure {
                    mail to: "marionmundara@gmail.com",
                    subject: "Test Stage - Status: Failure",
                    body: "Pipeline Failed in Test Stage!",
                    attachments: "${manager.build.logFile}"
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
                    subject: "Security Scan Stage - Status: Success",
                    body: "Pipeline Success in Security Scan Stage!",
                    attachments: "${manager.build.logFile}"
                }
                failure {
                    mail to: "marionmundara@gmail.com",
                    subject: "Security Scan Stage - Status: Failure",
                    body: "Pipeline Failed in Security Scan Stage!",
                    attachments: "${manager.build.logFile}"
                }
            }
        }
        stage('Deploy to Staging') {
            steps { 
                echo "Deploy the application to a staging server using deployment tool-  Docker."
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
