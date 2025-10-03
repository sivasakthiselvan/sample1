pipeline {
    agent any
    tools {
        jdk "jdk17"
        maven "Maven3"
    }
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps { bat 'mvn clean compile' }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
                junit '**/target/surefire-reports/*.xml'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package -DskipTests'
                archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
