pipeline {
    environment {
        registry = "kparun/demo"
        registryCredential = '11Learner1@'
        dockerImage = ''
    }
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

        stage('docker build/push") {
              docker.withRegistry("https://index.docker.io/v1/", "dockerhub") {
                  def app docker.build("kparun/nginx:${commit_id}", '.').push()
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
