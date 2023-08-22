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
			sh 'sudo docker build multibranch-sample .'
		}
	}
}