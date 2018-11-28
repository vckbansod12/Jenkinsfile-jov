#!/usr/bin/env groovy

pipeline {
	agent any 

	stages {
		stage ('Build') {			
			steps {
				setBuildStatus("Build complete", "SUCCESS")
			}															
		}
	}
}

def setBuildStatus(String message, String state) {	
	step([
		$class: "GitHubCommitStatusSetter",
		reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/vckbansod12/Jenkinsfile-jov"],
    		contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
   		errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      		statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
}
