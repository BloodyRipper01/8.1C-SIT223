pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "C:/Code/Proffessional Practice/6.1P"
        TESTING_ENVIRONMENT = "sandbox"
        PRODUCTION_ENVIRONMENT = "M.Sharkie"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${env.DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artefacts"
            }
        }
        stage('Test') {
            steps {
                echo "Preparing ${env.TESTING_ENVIRONMENT} for tests"
                echo "Unit tests"
                echo "Integration tests"
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Static analysis tools running..."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy the application to a testing environment: ${env.TESTING_ENVIRONMENT}"
            }
        }
        stage('Approval') {
            steps {
                sleep time: 10, unit: 'SECONDS'
            }
        }
        stage('Deploy to Product') {
            steps {
                echo "Deploying code to ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}
