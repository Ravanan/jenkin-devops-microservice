pipeline {	

		agent any
		//agent {docker {image 'maven:3.6.3'}}
		environment{
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage('Checkout')
			{
				steps{
					sh "mvn --version"
					echo "Build"	
					echo "PATH - $PATH"
					echo "BUILD_TAG - $env.BUILD_TAG"
					}
			}
			stage('Compile'){
				steps{
					sh "mvn clean compile"
				}
			}
			stage('Test')
			{
				steps{
					sh "mvn test"	
				}
			}
				stage('Integration Test')
			{
				steps{
					sh "mvn failsafe:integration-test failsafe:verify"	
				}
			}
		}

		post
		{
			always{
				echo ' am awesome'
			}
			success{
				echo 'sucess run'
			}
			failure{
				echo 'failed'
			}

		}
	
	}

