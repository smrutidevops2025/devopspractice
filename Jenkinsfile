pipeline {
    tools{
		jdk 'JAVA_HOME'
		maven 'M2_HOME'
	     }
    agent any

    stages {
			stage('checkout') {
            steps {
                git 'https://github.com/smrutidevops2025/devopspractice.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile '
            }
        }
		stage('test') {
            steps {
                sh 'mvn test'
            }
        }
		stage('package') {
            steps {
                sh 'mvn clean package '
		sh 'mv target/*.war target/webapp.war '
            }
        }
	    
	
      }
}
    
