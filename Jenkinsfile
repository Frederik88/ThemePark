pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
	dir('park'){
		stage('Build') {
            		steps {
                		sh './mvn compile'
            		}
        	}
        	stage('Test') {
            		steps {
                		sh './mvn test'
            		}
        	}
	}
    }
}