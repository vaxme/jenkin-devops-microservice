
//DECLARATIVE
pipeline {
	// agent any
	agent { docker { image 'maven:3.8.6'}}
	stages {
		stage ('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
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