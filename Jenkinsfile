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

       stage("Build image") {
            steps {
                script {
                    myapp = docker.build("rahulk2020/k8image:${env.BUILD_ID}")
                }
            }
        }      

       stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-rahulk') {
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }      


       stage('Deploy to GKE') {
            steps{
			    echo "Deployment started"
				sh 'ls -ltr'
				sh 'pwd'
                sh "sed -i 's/tagversion/${env.BUILD_ID}/g' deployment.yaml"
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: 'deployment.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
				echo "Deployment Finished"
            }
        }
  }
}
