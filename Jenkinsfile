pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        sh 'echo "hello world"'
        git(url: 'https://github.com/joopva/bWAPP.git', branch: 'mastr', credentialsId: 'github_usr')
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