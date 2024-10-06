pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    bat "echo 'Building the code...' >> ${LOG_FILE}"
                    // Uncomment and adjust based on your build
                    // bat 'gcc -o myProgram src/*.c >> ${LOG_FILE}' 
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
            script {
                echo 'Pipeline completed successfully.'
                bat "echo 'Pipeline completed successfully.' >> ${LOG_FILE}"
                sendEmailNotification(LOG_FILE)
            }
        }
        failure {
            script {
                echo 'Pipeline failed.'
                bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
                sendEmailNotification(LOG_FILE)
            }
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
            script {
                echo 'Pipeline completed successfully.'
                bat "echo 'Pipeline completed successfully.' >> ${LOG_FILE}"
                sendEmailNotification(LOG_FILE)
            }
        }
        failure {
            script {
                echo 'Pipeline failed.'
                bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
                sendEmailNotification(LOG_FILE)
            }
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
