// multistage
pipeline {
    agent any

        stages {
            stage('Source') {
                steps {
                    git url: 'https://github.com/kparunsagar/pipeline_springboot.git'
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
            stage ('Docker-copose')
          steps {
            sh '''
              docker compose version
            }
                  
        }
}
