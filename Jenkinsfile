pipeline{
	agent any
	stages{
		stage('Hello'){
			steps{
				echo "hello"
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
	}
}