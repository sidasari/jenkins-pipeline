//Declarative Pipeline
def VERSION='1.0.0'
pipeline {
    agent {
		docker { image 'maven:3.8.1-adoptopenjdk-11' }
		  }
      environment {
        PROJECT = "WELCOME TO DEVOPS B28 BATCH - Jenkins Class"
    }
    stages {
	    
        stage('mvn clean build') {
            
            steps { 
		git 'https://github.com/sidasari/jenkins-pipeline'
		 sh 'mvn --version'
                sh 'mvn clean install'
                // exit 1
            }
        }
    }
}


