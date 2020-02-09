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
               
        }
        stage('CD') {
                	steps {
                        echo 'Testing..'
                        sleep(9)

                              }
                    }





    }
}
