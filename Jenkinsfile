pipeline {
    agent any
    environment {
        PROJECT_ID = 'essential-oven-263421'
        CLUSTER_NAME = 'k8-cluster-rahulk'
        LOCATION = 'europe-west3-c'
        CREDENTIALS_ID = 'kubernetes'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }
		 stage("Build") {
            steps {
               echo "cleaning and packaging"
			   sh 'mvn clean package'
            }
        }
		 stage("Test") {
            steps {
                echo "Testing"
			   sh 'mvn test'
            }
        }

     }
}
