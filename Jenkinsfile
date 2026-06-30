pipeline {
    agent any

    tools {
        nodejs 'Node18'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Install Browsers') {
            steps {
                bat 'npx playwright install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npx playwright test'
            }
        }

    }

    post {

        always {
            archiveArtifacts artifacts: 'playwright-report/**', fingerprint: true
        }

        success {
            echo 'Build Passed'
        }

        failure {
            echo 'Build Failed'
        }

    }
}