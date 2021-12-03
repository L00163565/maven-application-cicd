pipeline {
    
	environment {
        registry = "https://hub.docker.com/"
        dockerImage = ""
    }
    agent any 
	
	tools {
        maven 'maven 3.8.4'
	'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'docker'
    }
    
    stages {
        
        stage('code checkout') {
            steps {
                git url: 'https://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@github.com/L00163565/maven-application-cicd.git'
            }
        }
		
        
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
	    stage('Build image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }

        stage('Push Image') {
            steps{
                script {
                docker.withRegistry( "" ) {
                    dockerImage.push()
                    }
                }
            }
        }
		
		stage('Deploy App') {
	        steps {
                script {
                    kubernetesDeploy(configs: "deployment.yaml", kubeconfigId: "mykubeconfig")
                }
            }
        }
    }
}
