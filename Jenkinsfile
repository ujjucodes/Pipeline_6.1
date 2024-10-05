pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    echo 'Cloning the Git repository...' | tee -a LOG_FILE
                    git 'https://github.com/ujjucodes/Pipeline_6.1.git' | tee -a LOG_FILE
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the code...' | tee -a LOG_FILE
                    bat 'gcc -o myProgram src/*.c' | tee -a LOG_FILE  // Adjust based on your build
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    echo 'Running unit tests...' | tee -a LOG_FILE
                    bat 'run_my_tests.bat' | tee -a LOG_FILE  // Adjust based on your testing command
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...' | tee -a LOG_FILE
                    bat 'run_code_analysis.bat' | tee -a LOG_FILE  // Adjust based on your analysis tool
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...' | tee -a LOG_FILE
                    bat 'deploy_to_staging.bat' | tee -a LOG_FILE  // Adjust based on your staging deployment
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on Staging...' | tee -a LOG_FILE
                    bat 'run_integration_tests.bat' | tee -a LOG_FILE  // Adjust based on your integration tests
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...' | tee -a LOG_FILE
                    bat 'deploy_to_production.bat' | tee -a LOG_FILE  // Adjust based on your production deployment
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.' | tee -a LOG_FILE
            sendEmailNotification(LOG_FILE)
        }
        failure {
            echo 'Pipeline failed.' | tee -a LOG_FILE
            sendEmailNotification(LOG_FILE)
        }
    }
}

// Function to send email notification
def sendEmailNotification(logFilePath) {
    emailext (
        subject: "Jenkins Pipeline - Execution Result",
        body: """The pipeline has finished. Please find the attached log file for details.""",
        attachLog: true,
        attachmentsPattern: logFilePath,
        to: "work.ujjwalds@gmail.com"  // Replace with the actual recipient email
    )
}
