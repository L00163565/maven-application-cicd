pipeline {
    
	environment {
        registry = "snehalshirsath/maven-app-image-lab3"
	registryCredential = 'docker_cred'
        dockerImage = ""
    }
    agent any 
	
	tools {
        maven 'maven 3.8.1'
	'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'docker'
    }
    
    stages {
        
        stage('code checkout') {
            steps {
                git url: 'https://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@github.com/L00163565/maven-application-cicd.git'
            }
        }
		
    }
}
