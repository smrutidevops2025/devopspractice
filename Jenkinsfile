pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/smrutidevops2025/devopspractice.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 sh "mv target/*.jar target/myweb.war"

		}
		}
   stage("deploy"){
	   steps{

      sshagent(['eb65e330-7301-4021-9be0-14e8209141f8']) {

	        sh """
                 
            scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@3.89.161.17:/home/ec2-user/tomcat10/webapps/

              ssh ec2-user@3.89.161.17 /home/ec2-user/tomcat10/bin/shutdown.sh
               ssh ec2-user@3.89.161.17 /home/ec2-user/tomcat10/bin/startup.sh
            
          
          """

}

	   
		}
		  
	  }


	
}
	}
	}
