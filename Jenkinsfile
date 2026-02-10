pipeline {
    agent any

    environment {
        APP_NAME = "my-web-app"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Checking out code from ${env.BRANCH_NAME}"
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
                sh 'echo "Compiling application..."'
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests"
                sh 'echo "All tests passed!"'
            }
        }

        stage('Code Quality') {
            steps {
                echo "Running static code analysis"
                sh 'echo "Quality gate passed"'
            }
        }

        stage('Deploy to Dev') {
            when {
                branch 'develop'
            }
            steps {
                echo "Deploying to DEV environment"
            }
        }

        stage('Deploy to Prod') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying to PRODUCTION environment"
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully 🚀"
        }
        failure {
            echo "Pipeline failed ❌"
        }
    }
}

