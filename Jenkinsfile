pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scm
                sh "MIX_ENV=test mix deps.get"
            }
        }
         stage('SonarQube analysis') {
             steps {
                script {
                      scannerHome = tool 'SonarQube Scanner 2.5'
                      echo "${scannerHome}"
                }
                withSonarQubeEnv('sonar') {
                   sh "${scannerHome}/bin/sonar-runner -e"
                }
             }
          }

    }
}
