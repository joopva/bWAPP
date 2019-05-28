pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        git(url: 'https://github.com/joopva/bWAPP.git', branch: 'master', credentialsId: 'github_usr')
      }
    }
    stage('scan') {
      steps {
        withSonarQubeEnv(installationName: 'scanner', credentialsId: 'sonarquebe') {
          waitForQualityGate(abortPipeline: true, credentialsId: 'sonarquebe')
        }

      }
    }
  }
}