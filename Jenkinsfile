#!/usr/bin/env groovy

pipeline {
	agent any 

	stages {
		stage ('Build') {			
			steps {
				sh './test'
				//setBuildStatus("Build complete", "FAILURE")
				setBuildStatus()
			}															
		}
	}
}

//def setBuildStatus(String message, String state) {	
//	step([
//		$class: "GitHubCommitStatusSetter",
//		reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/vckbansod12/Jenkinsfile-jov"],
//    		contextSource: [$class: "DefaultCommitContextSource"],
//		statusResultSource: [ $class: "ConditionalStatusResultSource"]
//      		statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
//    ]);
//}

def setBuildStatus() {	
	step([
		$class: "GitHubCommitStatusSetter",
		reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/vckbansod12/Jenkinsfile-jov"],
    		contextSource: [$class: "DefaultCommitContextSource"],
		statusResultSource: [ $class: "DefaultStatusResultSource"]
      		//statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
    ]);
}
