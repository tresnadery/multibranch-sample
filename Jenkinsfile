pipeline{
	agent any
	stages{
		stage('Hello'){
			steps{
				echo "hello world!"
			}
		}
		stage('Hello Development'){
			when{
				branch "development"
			}
			steps{
				echo "hello development"
			}
		}
		stage('build'){
			steps{
				sh "docker build --tag multibranch-sample:latest ."
				sh "docker tag multibranch-sample:latest ${env.CI_REGISTRY}/multibranch-sample:latest"				
			}
		}
		stage('publish'){
			steps{
				sh "echo ${env.CI_PASSWORD} | docker login -u ${env.CI_USER} --password-stdin ${env.CI_REGISTRY}"
				sh "docker ${env.CI_REGISTRY}/multibranch-sample:latest"
			}
		}
	}
}