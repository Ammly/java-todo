pipeline {
  agent any
  tools {
    gradle 'Gradle-6'
  }
  stages {
    stage('clone repository') {
        steps{
            git 'https://github.com/Ammly/java-todo'
        }
    }
    stage('Build') {
      steps {
        sh 'gradle build'
      }
    }

    stage('Test') {
      steps {
        sh 'gradle test'
      }
    }

    stage('Deploy to Heroku') {
      steps {
        withCredentials([usernameColonPassword(credentialsId: 'heroku', variable: 'HEROKU_CREDENTIALS' )]){
          sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/moringa-java-app.git master'
        }
      }
    }

  }
}