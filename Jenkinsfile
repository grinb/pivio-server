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
      stage('Docker build') {
        steps {
            script
            {
              docker.build("eran-pivio-server")
            }
        }
      }
      stage('Publish') {
           steps {
              script
	             {
                  docker.withRegistry("https://registry.hub.docker.com", "dockerHub")
		                {
                	   docker.image("eran-pivio-server").push()
                    }
              }
           }
      }
}
}
