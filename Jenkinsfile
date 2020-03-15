pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn clean'
        slackSend(
          teamDomain: "concordia-dkx2971",
          token:"UVm9cSlZCH4ikhzSLq3yun8w",
          channel:"#jenkins",
          color: "red",
          message: "Build done!"
        )
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
