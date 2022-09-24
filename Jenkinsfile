pipeline {
	environment {
	registry = "kparun/demo"
	registryCredential = 'kparun'
	dockerImage = ''
	}
	agent any
		stages {
			stage('Cloning our Git') {
				steps {
					git 'https://github.com/kparunsagar/Jenkins_docker_git.git'
				}
			}
			stage('Build image') {
            			steps{
                			script {
                        			app = docker.image("testproject/agent:latest")
                    			}
                		}
            		}
			stage('Deploy our image') {
				steps{
					script {
						docker.withRegistry( '', registryCredential ) {
						dockerImage.push()
						}
					}
				}
			}
			stage('Cleaning up') {
				steps{
					sh "docker rmi $registry:$kparun"
				}
			}
		}
}
