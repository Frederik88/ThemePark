pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    withSonarQubeEnv('My SonarQube Server', envOnly: true) {
        // This expands the evironment variables SONAR_CONFIG_NAME, SONAR_HOST_URL, SONAR_AUTH_TOKEN that can be used by any script.
        println ${ env.SONAR_HOST_URL }
    }
    
    stages {
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
