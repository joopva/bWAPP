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
        withSonarQubeEnv(installationName: 'scanner', credentialsId: 'sonarquebe')
        sh '''def scannerHome=tool(name: \'scanner\', type: \'hudson.plugins.sonar.SonarRunnerInstallation\')
        withSonarQubeEnv(installationName: \'scanner\', credentialsId: \'sonarquebe\') {
            sh \'${scannerHome}/bin/sonar-scanner -Dsonar.projectkey=123 -Dsonar.projectname=123 -Dsonar.source=.\'
        }'''
      }
    }
  }
}