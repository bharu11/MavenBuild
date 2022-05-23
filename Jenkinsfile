node('') {
	def sonarScanner = tool name: 'sonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
	stage ('checkout code'){
		checkout scm
	}
	
	stage ('Build'){
		 sh "mvn clean install -Dmaven.test.skip=true"
	}

	stage ('Test Cases Execution'){
		sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
	}

	stage ('Sonar Analysis'){
		withSonarQubeEnv(credentialsId: 'SonarQubeToken') {
			
}
		sh 'mvn sonar:sonar -Dsonar.host.url=http://3.86.225.3:9000/ -Dsonar.login=admin -Dsonar.password=password'
	}

	stage ('Deployment'){
		//ansiblePlaybook colorized: true, disableHostKeyChecking: true, playbook: 'deploy.yml'
	}
}
