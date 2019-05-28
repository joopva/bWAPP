pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        git(url: 'https://github.com/joopva/bWAPP.git', branch: 'master', credentialsId: 'github_usr')
      }
    }
    stage('test') {
      steps {
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'sonarquebe')
      }
    }
    stage('scan') {
      steps {
        waitForQualityGate(credentialsId: 'sonarquebe', abortPipeline: true)
      }
    }
  }
}