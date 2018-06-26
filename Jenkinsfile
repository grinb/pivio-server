pipeline {
    agent any
    stages {
      stage('checkout'){
        steps {
          checkout scm
        }
      }
      stage('Gradle Build') {
        steps {
          sh './gradlew build'
        }
      }
      stage('Build and Run Containers') {
        steps {
          sh './docker-compose up'
        }
      }
    }
}
