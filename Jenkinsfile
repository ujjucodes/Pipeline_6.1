pipeline {
    agent any
    
    environment {
        EMAIL_RECIPIENT = 'work.ujjwalds@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the code using Maven...'
                    // Tool: Maven
                    sh 'mvn clean package'
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    // Tool: JUnit or TestNG
                    sh 'mvn test'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing code with SonarQube...'
                    // Tool: SonarQube
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan with OWASP ZAP...'
                    // Tool: OWASP ZAP
                    sh 'zap.sh -cmd -quickurl http://your-app-url -quickout zap_report.html'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying application to staging server...'
                    // Tool: AWS CLI or Ansible
                    sh 'aws s3 cp target/your-app.jar s3://your-staging-bucket/'
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Tool: Postman or Selenium
                    sh 'newman run collection.json'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying application to production server...'
                    // Tool: AWS CLI or Ansible
                    sh 'aws s3 cp target/your-app.jar s3://your-production-bucket/'
                }
            }
        }
    }

    post {
        success {
            script {
                echo 'Pipeline completed successfully.'
            }
            // Send email on success
            mail to: 'work.ujjwalds@gmail.com',
                 subject: "Build Successful: ${currentBuild.fullDisplayName}",
                 body: "The build was successful. Check the console output at ${env.BUILD_URL}."
        }
        failure {
            script {
                echo 'Pipeline failed.'
            }
            // Send email on failure
            mail to: "${work.ujjwalds@gmail.com}",
                 subject: "Build Failed: ${currentBuild.fullDisplayName}",
                 body: "The build failed. Check the console output at ${env.BUILD_URL}."
        }
    }
}
