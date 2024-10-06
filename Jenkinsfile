pipeline {
    agent any
    environment {
        LOG_FILE = "pipeline_log.txt"  // Define the log file name
    }

    stages {  
        stage('Notify Pipeline Created') {
            steps {
                script {
                    echo 'Pipeline has been created and started successfully.'
                    emailext (
                        subject: "Jenkins Pipeline Created",
                        body: "The Jenkins pipeline has been created and started.",
                        to: "work.ujjwalds@gmail.com"
                    )
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    bat "echo 'Building the code...' >> ${LOG_FILE}"
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
                emailext (
                    subject: "Jenkins Pipeline - Success",
                    body: "The Jenkins pipeline has completed successfully.",
                    attachmentsPattern: LOG_FILE,
                    to: "work.ujjwalds@gmail.com"
                )
            }
        }
        failure {
            script {
                echo 'Pipeline failed.'
                bat "echo 'Pipeline failed.' >> ${LOG_FILE}"
                emailext (
                    subject: "Jenkins Pipeline - Failure",
                    body: "The Jenkins pipeline has failed. Please check the attached log.",
                    attachmentsPattern: LOG_FILE,
                    to: "work.ujjwalds@gmail.com"
                )
            }
        }
    }
}
