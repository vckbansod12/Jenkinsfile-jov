#!/usr/bin/env groovy

pipeline {
	agent any 

	stages {
		stage ('Build') {			
			steps {
				//sh './Hello.sh'
				echo 'Hello'								
			}															
		}
		
	}
	post {
		success {
			setBuildStatus("Build complete", "SUCCESS")
		}
		failure {
			setBuildStatus("Build failed", "FAILURE")
		}
	}	

}

def setBuildStatus(String message, String state) {	
	step([
		$class: "GitHubCommitStatusSetter",
		reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/vckbansod12/Jenkinsfile-jov"],
    		contextSource: [$class: "DefaultCommitContextSource"],
      		statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
}
