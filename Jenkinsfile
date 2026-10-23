pipeline {
	agent any

	stages {
		stage('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/dev-aryankapoor/calculator-cicd.git'
			}		
		}	


		stage('Build - Setup Environment') {
			steps {
				sh 'python -m venv venv'
				sh './venv/bin/pip install -r requirements.txt'	
			}		
		}

		stage('Test') {
			steps {
				sh './venv/bin/pytest test_calculator.py -v'	
			}		
		}


		stage('Deploy') {
			steps {
				echo 'Deploying Calculator App...'
				sh './venv/bin/python calculator.py'	
			}		
		}
	}

	post {
		success {
			echo 'Pipeline completed successfully!'
		}

		failure {
			echo 'Pipeline failed. Check logs above.'
		}
	}
}
