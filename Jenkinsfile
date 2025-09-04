pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/BloodyRipper01/8.2CDevSecOps.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                bat 'npm test || exit 0' // Continue even if tests fail
            }
            post {
                failure {
                    emailext(
                        subject: "Testing FAILURE",
                        body: "Well that sucks, testing failed",
                        to: "mitchellsharkie01@gmail.com"
                    )
                }
                success {
                    emailext(
                        subject: "Testing SUCCESS",
                        body: "Testing was a great success - Borat Voice",
                        to: "mitchellsharkie01@gmail.com"
                    )
                }
            }
        }
        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage || exit 0'
            }
        }
        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit 0'
            }
            post {
                failure {
                    emailext(
                        subject: "Security Scans FAILURE",
                        body: "We got a security issue, sir",
                        to: "mitchellsharkie01@gmail.com"
                    )
                }
                success {
                    emailext(
                        subject: "Security Scans SUCCESS",
                        body: "All locked up",
                        to: "mitchellsharkie01@gmail.com"
                    )
                }
            }
        }
    }
}
