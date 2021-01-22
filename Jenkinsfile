pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
		stage('Build') {
            steps {
				dir('park'){
                	sh './mvn compile'
				}
            }
        }
        stage('Test') {
            steps {
				dir('park'){
                	sh './mvn test'
				}
            }
        }
    }
}