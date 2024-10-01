pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    echo 'Cloning the Git repository...'
                    git 'https://github.com/ujjucodes/Pipeline_6.1.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the code...'
                    // Assuming your project has a Makefile or a build script, run the appropriate build command
                    bat 'gcc -o myProgram src/*.c'  // Example for compiling C code (adjust as needed)
                    // If using Java without Maven, you can compile with javac: bat 'javac -d bin src/**/*.java'
                }
            }
        }

        stage('Unit Tests') {
            steps {
                script {
                    echo 'Running unit tests...'
                    // Add your custom testing script or tool command here
                    bat 'run_my_tests.bat'  // Replace with your actual test execution command
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis...'
                    // Add any code analysis tool you are using (SonarQube, Lint, etc.)
                    bat 'run_code_analysis.bat'  // Replace with your actual code analysis command
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...'
                    // Add your staging deployment script here
                    bat 'deploy_to_staging.bat'  // Replace with your deployment script or commands
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on Staging...'
                    // Add your integration testing script here
                    bat 'run_integration_tests.bat'  // Replace with the actual test command
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...'
                    // Add your production deployment script here
                    bat 'deploy_to_production.bat'  // Replace with the actual deployment script or commands
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
            // Optionally, add email or other notification methods
        }
    }
}
