pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['dev', 'prod'],
            description: 'Select environment to deploy'
        )
    }

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
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
            }
        }

        stage('Deploy') {
            when {
                expression { params.ENV == 'prod' && env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Deploying ${APP_NAME} to PRODUCTION"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished for ${params.ENV}"
        }
    }
}

