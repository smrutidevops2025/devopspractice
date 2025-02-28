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
	stage("deploy"){
	   steps{

      sshagent(['deployment']) {

	        sh """
                 
            scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.12.90:/home/ec2-user/tomcat10/webapps/

              ssh ec2-user@172.31.12.90 /home/ec2-user/tomcat10/bin/shutdown.sh
               ssh ec2-user@172.31.12.90 /home/ec2-user/tomcat10/bin/startup.sh
            
          
          """

}

	   
		}
		  
	  }
  
	
      }
}
    
