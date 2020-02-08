pipeline {
    agent any

    stages {
        stage('CI') {
            steps {
                echo 'Building..'
                  mvn package
            }
        }
        stage('CD') {
            steps {
                echo 'Testing..'
            }
        }
    }
}
