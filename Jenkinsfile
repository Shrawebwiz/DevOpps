pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // or the name you configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Shrawebwiz/DevOpps.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}