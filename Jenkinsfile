pipeline {
	agent
	{
        docker { 
                 image "tomcat/jdk:latest"
                 registryUrl 'https://index.docker.io/v1/'
                 registryCredentialsId "docker_usr"
                 reuseNode true
               }
    	} 
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
