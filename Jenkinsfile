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
				sh 'sudo docker build multibranch-sample:latest .'
				sh 'sudo docker multibranch-sample:latest ${env.CI_REGISTRY}/multibranch-sample:latest'				
			}
		}
		stage('publish'){
			steps{
				sh 'echo ${env.CI_PASSWORD} | sudo docker login -u ${env.CI_USER} --password-stdin ${env.CI_REGISTRY}'
				sh 'sudo docker ${env.CI_REGISTRY}/multibranch-sample:latest'
			}
		}
	}
}