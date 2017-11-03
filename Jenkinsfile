pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               node {
                    checkout scm
                    sh "MIX_ENV=test mix deps.get"
                }
            }
        }
         stage('SonarQube analysis') {
             steps {
                script {
                      scannerHome = tool 'SonarQube Scanner 2.5'
                      echo "${scannerHome}"
                }
                withSonarQubeEnv('sonar') {
                   sh "${scannerHome}/bin/sonar-runner -e -Dsonar.host.url=http://localhost:9000/sonar/"
                }
             }
          }

    }
}
