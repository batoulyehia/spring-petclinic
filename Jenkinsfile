pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat './mvnw package' 
            }
        }
        stage('Test') { 
            steps { 
                mvn clean test
            }
        }
    }
}
