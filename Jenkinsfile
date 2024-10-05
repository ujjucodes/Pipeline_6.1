pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    // stages {
    //     stage('Checkout') {
    //         steps {
    //             script {
    //                 echo 'Cloning the Git repository...' 
    //                 bat "echo 'Cloning the Git repository...' >> ${LOG_FILE}"
    //                 git 'https://github.com/ujjucodes/Pipeline_6.1.git' 
    //             }
    //         }
    //     }

        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    bat "echo 'Building the code...' >> ${LOG_FILE}"
                    bat 'gcc -o myProgram src/*.c >> ${LOG_FILE}'  // Adjust based on your build
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    echo 'Running unit tests...'
                    bat "echo 'Running unit tests...' >> ${LOG_FILE}"
                    bat 'run_my_tests.bat >> ${LOG_FILE}'  // Adjust based on your testing command
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...'
                    bat "echo 'Performing code analysis...' >> ${LOG_FILE}"
                    bat 'run_code_analysis.bat >> ${LOG_FILE}'  // Adjust based on your analysis tool
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...'
                    bat "echo 'Deploying to Staging...' >> ${LOG_FILE}"
                    bat 'deploy_to_staging.bat >> ${LOG_FILE}'  // Adjust based on your staging deployment
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on Staging...'
                    bat "echo 'Running integration tests on Staging...' >> ${LOG_FILE}"
                    bat 'run_integration_tests.bat >> ${LOG_FILE}'  // Adjust based on your integration tests
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...'
                    bat "echo 'Deploying to Production...' >> ${LOG_FILE}"
                    bat 'deploy_to_production.bat >> ${LOG_FILE}'  // Adjust based on your production deployment
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
            bat "echo 'Pipeline completed successfully.' >> ${LOG_FILE}"
            sendEmailNotification(LOG_FILE)
        }
        failure {
            echo 'Pipeline failed.'
            bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
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
