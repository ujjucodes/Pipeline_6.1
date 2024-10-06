pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    // Send an email at the start of the pipeline creation
    options {
        skipDefaultCheckout()
    }
    
    stages {
        stage('Notify Pipeline Created') {
            steps {
                script {
                    echo 'Pipeline has been created and started successfully.'
                    sendPipelineCreationNotification()
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    bat "echo 'Building the code...' >> ${LOG_FILE}"
                    // Uncomment to actually run the build
                     bat 'gcc -o myProgram src/*.c >> ${LOG_FILE}'  // Adjust based on your build
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    echo 'Running unit tests...'
                    bat "echo 'Running unit tests...' >> ${LOG_FILE}"
                    // Uncomment to actually run unit tests
                     bat 'run_my_tests.bat >> ${LOG_FILE}'  // Adjust based on your testing command
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...'
                    bat "echo 'Performing code analysis...' >> ${LOG_FILE}"
                    // Uncomment to actually run code analysis
                    bat 'run_code_analysis.bat >> ${LOG_FILE}'  // Adjust based on your analysis tool
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...'
                    bat "echo 'Deploying to Staging...' >> ${LOG_FILE}"
                    // Uncomment to actually deploy to staging
                     bat 'deploy_to_staging.bat >> ${LOG_FILE}'  // Adjust based on your staging deployment
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on Staging...'
                    bat "echo 'Running integration tests on Staging...' >> ${LOG_FILE}"
                    // Uncomment to actually run integration tests
                     bat 'run_integration_tests.bat >> ${LOG_FILE}'  // Adjust based on your integration tests
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...'
                    bat "echo 'Deploying to Production...' >> ${LOG_FILE}"
                    // Uncomment to actually deploy to production
                     bat 'deploy_to_production.bat >> ${LOG_FILE}'  // Adjust based on your production deployment
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
            bat "echo 'Pipeline completed successfully.' >> ${LOG_FILE}"
            sendEmailNotification(LOG_FILE, true)
        }
        failure {
            echo 'Pipeline failed.'
            bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
            sendEmailNotification(LOG_FILE, false)
        }
    }
}

// Function to send email when the pipeline is created successfully
def sendPipelineCreationNotification() {
    emailext (
        subject: "Jenkins Pipeline - Pipeline Creation Success",
        body: """The Jenkins pipeline has been created and started successfully. The build is now in progress.""",
        to: "work.ujjwalds@gmail.com"  // Replace with the actual recipient email
    )
}

// Function to send email notification after pipeline completion
def sendEmailNotification(logFilePath, isSuccess) {
    def subjectLine = isSuccess ? "Jenkins Pipeline - Execution Success" : "Jenkins Pipeline - Execution Failed"
    def bodyText = isSuccess ? "The pipeline has completed successfully. Please find the attached log file for details." 
                             : "The pipeline has failed. Please find the attached log file for details."

    emailext (
        subject: subjectLine,
        body: bodyText,
        attachLog: true,
        attachmentsPattern: logFilePath,
        to: "work.ujjwalds@gmail.com"  // Replace with the actual recipient email
    )
}
