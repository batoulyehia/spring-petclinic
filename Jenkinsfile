pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn clean'
        slackSend(teamDomain: 'concordia-dkx2971', token: 'UVm9cSlZCH4ikhzSLq3yun8w', channel: '#jenkins', color: 'good', message: 'Build started.')
      }
      post {
        success {
          slackSend(teamDomain: 'concordia-dkx2971', token: 'UVm9cSlZCH4ikhzSLq3yun8w', channel: '#jenkins', color: 'good', message: 'Build Successful!')
        }

        failure {
          slackSend(teamDomain: 'concordia-dkx2971', token: 'UVm9cSlZCH4ikhzSLq3yun8w', channel: '#jenkins', color: 'danger', message: 'Build Failed!')
        }
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
