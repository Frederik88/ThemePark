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
                    sh "${scannerHome}/park/sonar-scanner"
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
