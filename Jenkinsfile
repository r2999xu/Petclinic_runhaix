pipeline {
  agent any

  tools {
    maven 'Maven'
  }

  stages {
    stage('Build') {
      steps {
        sh './mvnw clean install'
      }
    }

    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('My SonarQube Server') {
          sh './mvnw sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=admin -Dsonar.password=admin'
        }
      }
    }
  }
}
