pipeline{
	agent {
		dockerfile true
	}
	stages {
		stage('Build') {
			steps {
				sh 'docker compose up -d --no-color --wait'
                        	sh 'docker compose ps'
			}
		}
	}
}
