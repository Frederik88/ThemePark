pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
		stage('Build') {
            steps {
				dir('park'){
                	sh 'mvn compile'
				}
            }
        }
        stage('Test') {
            steps {
				dir('park'){
                	sh 'mvn test'
				}
            }
        }
    }
}