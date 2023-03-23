pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull alfarazi11/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up automation-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"
			bat "sudo rm -rf output/"
		}
	}
}