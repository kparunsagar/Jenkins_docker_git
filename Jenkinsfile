pipeline {
	environment {
	registry = "kparun/demo"
	registryCredential = '11Learner1@'
	dockerImage = ''
	}
	agent any
		stages {
			stage('Cloning our Git') {
				steps {
					git 'https://github.com/kparunsagar/Jenkins_docker_git.git'
				}
			}
			stage('Building our image') {
				steps{
					script {
						dockerImage = docker.build registry + ":$kparun"
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
