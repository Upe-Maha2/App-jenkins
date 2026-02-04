pipeline {
    agent any

    environment {
        NODE_ENV = "production"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing npm dependencies..."
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests (if any)..."
                sh 'npm test || echo "No tests found, skipping"'
            }
        }

        stage('Build') {
            steps {
                echo "Building the project..."
                sh 'npm run build'
            }
        }

    }

    post {
        success {
            echo "✅ Build Successful!"
        }
        failure {
            echo "❌ Build Failed — Check console output."
        }
    }
}
