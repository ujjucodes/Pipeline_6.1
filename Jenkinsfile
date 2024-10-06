pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    stages {  // Ensure the stages block is included
        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    bat "echo 'Building the code...' >> ${LOG_FILE}"
                    // bat 'gcc -o myProgram src/*.c >> ${LOG_FILE}'  // Adjust based on your build
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    echo 'Running unit tests...'
                    bat "echo 'Running unit tests...' >> ${LOG_FILE}"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...'
                    bat "echo 'Performing code analysis...' >> ${LOG_FILE}"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...'
                    bat "echo 'Deploying to Staging...' >> ${LOG_FILE}"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on Staging...'
                    bat "echo 'Running integration tests on Staging...' >> ${LOG_FILE}"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...'
                    bat "echo 'Deploying to Production...' >> ${LOG_FILE}"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
            bat "echo 'Pipeline completed successfully.' >> ${LOG_FILE}"
            sendEmailNotification("Pipeline Successful")
        }
        failure {
            echo 'Pipeline failed.'
            bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
            sendEmailNotification("Pipeline Failed")
        }
    }
}

// Function to send email notification
def sendEmailNotification(status) {
    emailext (
        subject: "Jenkins Pipeline - ${status}",
        body: "${status},'Please check the detailed status of failure / success in the log'",
        attachLog: true,
        attachmentsPattern: LOG_FILE,
        to: "work.ujjwalds@gmail.com"  // Replace with the actual recipient email
    )
}
