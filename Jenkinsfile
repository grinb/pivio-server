pipeline {
  agent
    {
        node
        {
            label 'generic'
          }
        }
    stages {
      stage('checkout'){
        steps {
          checkout scm
        }
      }
      stage('Gradle Build') {
        steps {
          sh 'java -version'
          sh './gradlew build -x test'
        }
      }
      stage('Build and Run Containers') {
        steps {
          sh 'docker-compose up'
        }
      }
    }
}
