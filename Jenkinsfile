// multistage
pipeline {
    agent any

        stages {
            stage('Source') {
                steps {
                    git url: 'https://github.com/kparunsagar/Jenkins_docker_git.git'
                }
            }
            stage('Build') {
                steps {
                    script {
                        def mvnHome = tool 'maven'
                        bat "${mvnHome}\\bin\\mvn -B verify"
                    }
                }
            }
                             
        }
}
