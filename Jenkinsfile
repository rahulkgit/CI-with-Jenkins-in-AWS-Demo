pipeline {
    agent any

      tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "MAVEN_LATEST"
   }
    stages {
        stage('CI') {
            steps {
                echo 'Building..'
                sh "mvn package"            

                  }
               
             post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
            success {
               archiveArtifacts 'target/*.war'
            }
        }
        stage('CD') {
            steps {
                echo 'Testing..'


            }
        }
    }
}
