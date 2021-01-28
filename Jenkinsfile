pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage('Sonarqube') {
            environment {
                scannerHome = tool 'Sonar Scanner'
            }
            steps {
                withSonarQubeEnv('SonarQube') {
                    dir('park'){
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                dir('park') {
                    sh 'mvn compile'
                }
            }
        }
        stage('Test') {
            steps {
                dir('park') {
                    sh 'mvn test'
                }
            }
        }
    }
}
