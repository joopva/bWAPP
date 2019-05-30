pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        git(url: 'https://github.com/joopva/bWAPP.git', branch: 'master', credentialsId: 'github')
      }
    }
    stage('scan') {
      steps {
        sh '''def scannerHome=tool(name: \'scanner\', type: \'hudson.plugins.sonar.SonarRunnerInstallation\')
       
withSonarQubeEnv(installationName: \'sonarqube\', credentialsId: \'sonarquebe\') {
            sh \'${scannerHome}/bin/sonar-scanner -Dsonar.projectkey=123 -Dsonar.projectname=123 -Dsonar.source=.\'
        }'''
      }
    }
  }
}