pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git url: 'https://github.com/lmaoggrofl/JenkinsDependencyCheckTest.git', branch: 'master'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--nvdApiKey "176cfd53-8ad1-40bd-a460-c10570a164d6" --format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
