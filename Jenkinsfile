pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    stages {
        stage('SonarQube analysis') {
            steps {
                scannerHome = tool 'SonarScanner 4.6'
                withSonarQubeEnv('SonarQube', envOnly: true) {
                    // This expands the evironment variables SONAR_CONFIG_NAME, SONAR_HOST_URL, SONAR_AUTH_TOKEN that can be used by any script.
                    println ${ env.SONAR_HOST_URL }
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
