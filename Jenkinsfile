pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "No build needed (static HTML project)."
            }
        }

        stage('Test') {
            steps {
                echo "No tests defined."
            }
        }

        stage('Archive') {
            steps {
                echo "Archiving HTML file..."
                archiveArtifacts artifacts: '**/*.html', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "✅ Build finished successfully!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}
