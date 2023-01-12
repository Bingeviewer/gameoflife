pipeline {
	agent {
		node {
			label 'built-in'
		}
	}
	tools {
		jdk "jdk1.8"
		maven "maven"
	}
	stages {
		stage('git fetch') {
			steps {
				git branch: "master" , url: 'git@github.com:Bingeviewer/gameoflife.git' , credentialId: "bingeviewer"
			}
		}
		stage('building war') {
			steps {
				sh "mvn clean package"
			}
		}
		stage('deploying container') {
			steps {
				sh "docker-compose up -d"
			}
		}
	}
}
