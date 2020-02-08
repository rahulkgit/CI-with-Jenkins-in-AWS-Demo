pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                echo 'Building..'
                 withMaven(maven : 'MAVEN_LATEST')
                {
                   sh ' mvn package'
                } 
            }
        }
        stage('CD') {
            steps {
                echo 'Testing..'
            }
        }
    }
}
