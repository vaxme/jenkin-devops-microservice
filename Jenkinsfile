
//DECLARATIVE
pipeline {
	agent any
	//agent { docker { image 'maven:3.8.6'}}
	//agent { docker { image 'node:19.0.0'}}
	environment {
		dockerHome = tool 'MyDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BuilD_ID - $env.BuilD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BuilD_TAG - $env.BuilD_TAG"
				echo "BuilD_URL - $env.BuilD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}

		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image') {
			steps {
			//"docker build -t vaxme/currency-exchange-devops:$env.BuilD_TAG"
			script {
				dockerImage = docker.build("vaxme/currency-exchange-devops:{$env.BuilD_TAG}")
			}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
					dockerImage.Push();
					dockerImage.Push('latest');
					}
				}
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