pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn clean'
        slackSend(username: 'SlackBot', tokenCredentialId: 'UVm9cSlZCH4ikhzSLq3yun8w', teamDomain: 'concordia-dkx2971', channel: 'jenkins', color: 'black', failOnError: true, message: 'Build Done')
      }
    }

    stage('Test') {
      steps {
        bat 'mvn test'
      }
    }

    stage('Package') {
      steps {
        bat 'mvn package'
      }
    }

    stage('Deploy') {
      when {
        branch 'master'
      }
      steps {
        bat 'mvn deploy'
      }
    }

  }
}