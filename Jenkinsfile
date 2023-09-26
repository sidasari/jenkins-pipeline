//Declarative Pipeline
def VERSION='1.0.0'
pipeline {
    agent none
    // tools {
	//  maven 'apache-maven-3.6.3'
    // }
    environment {
        PROJECT = "WELCOME TO DEVOPS B28 BATCH - Jenkins Class"
    }
    stages {
        stage("Tools initialization") {
            agent { label 'DEV' }
            steps {
               
                sh "java -version"
            }
        }
        stage('mvn clean build') {
             agent {
				docker { image 'maven:3.8.1-adoptopenjdk-11' }
				}
            steps { 
                sh "mvn clean install"
                // exit 1
            }
        }
       
         stage('docker build') {
            agent { label 'DEV' }
            steps { 
                sh "sudo docker build -t sreeharshav/devopsb28spring:$BUILD_NUMBER ."
            }
        }
        stage('Deploy Docker Image') {
            agent { label 'DEV' }
            steps { 
                sh "sudo docker stop springbootapp || sudo docker ps"
                sh "sudo docker run --rm -dit --name springbootapp -p 8080:8080 sreeharshav/devopsb28spring:$BUILD_NUMBER"
            }
        }
        stage('Validate Deployment') {
            options {
               timeout(time: 3, unit: 'MINUTES') 
            }
            agent { label 'DEV' }
            steps { 
                sh "sleep 30 && curl http://ec2-34-201-18-149.compute-1.amazonaws.com:8080 || exit 1"
            }
        }
    }
   

}


