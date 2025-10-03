pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code..."
                checkout scm
            }
        }

        stage('Show HTML') {
            steps {
                echo "Displaying contents of sample.html"
                bat 'type sample.html'
            }
        }

        stage('Open HTML') {
            steps {
                echo "Opening HTML file in default browser..."
                bat 'start sample.html'
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
            echo "✅ HTML build completed successfully!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}
