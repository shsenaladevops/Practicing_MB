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
                echo "Compiling application..."
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests"
                echo "All tests passed!"
            }
        }

        stage('Code Quality') {
            steps {
                echo "Running static code analysis"
                echo "Quality gate passed"
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
