pipeline {
    agent any
    stages {
        stage('Build') { 
            steps { 
                echo "Use a build automation tool- Maven to compile and package the code."
            }
            
            post {
                success {
                    mail to: "marionmundara@gmail.com",
                    subject: "The build status",
                    body: "build status is a success!"
                }
            }
        } // Close stage('Build')

        stage('Unit and Integration Tests') {
            steps { 
                echo " Use test automation tool- Junit for unit tests and integration test purposes."
            }
        } // Close stage('Unit and Integration Tests')

        stage('Code Analysis') {
            steps { 
                echo " Integrate a code analysis tool- SonarQube."
            }
        } // Close stage('Code Analysis')

        stage('Security Scan') {
            steps { 
                echo " Perform a security scan using a tool- OWASP ZAP."
            }
        } // Close stage('Security Scan')

        stage('Deploy to Staging') {
            steps { 
                echo "Deploy the application to a staging server using deployment tool-  Docker."
            }
        } // Close stage('Deploy to Staging')

        stage('Integration Tests on Staging') {
            steps { 
                echo "Run integration tests on the staging environment."
            }
        } // Close stage('Integration Tests on Staging')

        stage('Deploy to Production') {
            steps { 
                echo " Deploy the application to a production server using deployment tool- Docker."
            }
        } // Close stage('Deploy to Production')

    } // Close stages
} // Close pipeline
