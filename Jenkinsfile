#!/usr/bin/env groovy

pipeline {
	agent any 

	stages {
		stage ('Build') {
			setBuildStatus("Build complete", "SUCCESS")														
		}
	}
}

def setBuildStatus(String message, String state) {	
	steps([
		$class: "GitHubCommitStatusSetter",
		reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/my-org/my-repo"],
    		contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
   		errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      		statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
}
