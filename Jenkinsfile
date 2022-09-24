pipeline {
  agent {
    docker {
      image 'mysql:latest'
    }
  }

  stages {
    stage('SCM') {
        steps {
      		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/kparunsagar/Jenkins_docker_git.git']]])
	      }
    }

    stage('Build') {
          steps {
               sh 'mvn compile'
          }
    }

    stage('Publish') {
          steps {
    	      sh 'mvn test'
          }
    }
  }
}
