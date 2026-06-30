pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'node -v'
                bat 'npm -v'
                bat 'npm ci'
            }
        }

        stage('Run Tests') {
            steps {
                bat "npx playwright test --project=%BROWSER%"
            }
        }
    }
}