node ('MAVEN') {

	stage ('SCM') {
		// git clone
		git branch: 'master', url: 'https://github.com/kumar212/openmrs-core.git'
	}
	
	stage ('build') {
		// build the package
		sh 'mvn package'
	}
	
	stage ('SonarQube analysis') {
        // performing sonarqube analysis        
        withSonarQubeEnv('SONAR') {        
        sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'        
       }
    }

	stage ('archival') {
		// archiving artifacts
		archiveArtifacts artifacts: 'target/*.jar'
	}

}	
