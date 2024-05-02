pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Build stage - Compiling and packaging code with Maven.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Unit and Integration Tests stage - Running tests with JUnit.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code Analysis stage - Analyzing code with SonarQube.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Security Scan stage - Scanning code with OWASP Dependency-Check.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploy to Staging stage - Deploying to staging server with Ansible.'
            }
        }
        stage('Staging Integration Tests') {
            steps {
                echo 'Staging Integration Tests stage - Running tests with Selenium in staging.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploy to Production stage - Deploying to production server with Ansible.'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
        success{
            mail to: "zjrderek@gmail.com",
            subject: "Build Status Email",
            body: "Build was successful!"
        }
    }
}