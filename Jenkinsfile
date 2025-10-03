pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Serve HTML') {
            steps {
                echo "Starting local web server on http://localhost:8000"
                // Kill any existing python server first
                bat 'taskkill /F /IM python.exe /T || exit 0'
                
                // Start Python HTTP server in background
                bat 'start /B python -m http.server 8000'
            }
        }
    }

    post {
        success {
            echo "✅ HTML is now being served at: http://localhost:8000/sample.html"
        }
        failure {
            echo "❌ Failed to serve HTML file"
        }
    }
}
