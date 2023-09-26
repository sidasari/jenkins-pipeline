//Declarative Pipeline
def VERSION='1.0.0'
pipeline {
    agent none
      environment {
        PROJECT = "WELCOME TO DEVOPS B28 BATCH - Jenkins Class"
    }
    stages {
        stage('mvn clean build') {
             agent {
		docker { image 'maven:3.8.1-adoptopenjdk-11' }
		  }
            steps { 
                sh 'mvn clean install'
                // exit 1
            }
        }
    }
}


