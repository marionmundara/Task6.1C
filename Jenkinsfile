pipeline {
    agent any
    stages {
        stage('Build') { 
            steps { 
                echo "Use a build automation tool- Gradle to compile and package the code."
            }
            
            post {
                success {
                    emailext to: "marionmundara@gmail.com",
                    subject: "Status",
                    body: "Pipeline Success!",
                    attachLog: true
                }
               failure {
                      emailext to: 'marionmundara@gmail.com',
                      subject: "Status",
                      body: "Pipeline Failed",
                      attachLog: true
                } 
            }
        }

        stage('Unit and Integration Tests') {
            steps { 
                echo " Use test automation tool- Junit for unit tests and integration test purposes."
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
