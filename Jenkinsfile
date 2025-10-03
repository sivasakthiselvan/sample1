pipeline {
    agent any

    environment {
        // Optional: specify Python path if needed
        PYTHON_HOME = "C:\\Python39" 
        PATH = "${env.PYTHON_HOME};${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out source code from GitHub..."
                checkout scm
            }
        }

        stage('Show HTML') {
            steps {
                echo "Printing contents of sample.html"
                bat 'type sample.html'
            }
        }

        stage('Archive HTML') {
            steps {
                echo "Archiving sample.html as build artifact..."
                archiveArtifacts artifacts: 'sample.html', fingerprint: true
            }
        }

        stage('Optional: Serve HTML via Python') {
            steps {
                echo "Starting local Python HTTP server (temporary)..."
                // Note: Jenkins service may not allow GUI browser opening
                bat 'start /B python -m http.server 8000'
                echo "Python server running at http://localhost:8000/sample.html"
            }
        }

        stage('Optional: Deploy to IIS') {
            steps {
                echo "Copying sample.html to IIS wwwroot..."
                bat 'copy /Y sample.html C:\\inetpub\\wwwroot\\sample.html'
                echo "HTML deployed: http://localhost/sample.html"
            }
        }
    }

    post {
        success {
            echo "✅ Build completed successfully!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}
