pipeline {
    agent any

    environment {
        APP_NAME = 'jenkins-app'
        BUILD_VERSION = '1.0'
    }

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: 'Select the deployment environment'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
                echo "Build Version: ${BUILD_VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"
            }
        }

        stage('Test') {
            steps {
                echo 'Running application tests'
                sh 'echo "Test completed successfully"'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying ${APP_NAME}"
                echo "Target Environment: ${params.ENVIRONMENT}"
            }
        }
    }

    post {

        always {
            echo 'Pipeline execution completed'
        }

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        cleanup {
            echo 'Cleanup completed'
        }
    }
}
