pipeline {
    agent any
    stages {

        stage('Deploy'){
        	steps {
                sh "docker compose up -d"
        	}
        }      
        stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Labtest1'
			}
		}
    }   
    post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
