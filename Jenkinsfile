pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/dockerproject']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/kparunsagar/Jenkins_docker_git.git']]])
            }
        }
        stage('Build image') {
            steps{
                script {
                        app = docker.image("mysql:latest")
                    }
                }
            }

        
        stage('Check Image') {
            steps {
                script {
                    app.inside() {
                        sh 'pwd'
                        sh 'java --version'
                    }
                }
            }
        }
    }
}
