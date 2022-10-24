
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.8.6'}}
	//agent { docker { image 'node:19.0.0'}}
	stages {
		stage ('Build') {
			steps {
				//sh 'mvn --version'
				//sh 'node --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BuilD_ID - $env.BuilD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BuilD_TAG - $env.BuilD_TAG"
				echo "BuilD_URL - $env.BuilD_URL"
			}
		}
		stage ('Test') {
			steps {
				echo "Test"
				}
		}
		stage ('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
		}
	post {
		always {
			echo 'Im awesome'
		}
		success {
			echo 'I run when succesful'
		}
		failure {
			echo 'I run when u failed'
		}
	}
}