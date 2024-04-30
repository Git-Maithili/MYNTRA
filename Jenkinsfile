pipeline {
	agent any
	
	parameters {
             choice(name: 'choice', choices: ['QA', 'UAT', 'DEV'], description: 'This is for Choice Parameter') 
        }
        stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
	    stage('Build') {
	         steps {
		      sh '/home/vboxuser/Documents/DevOps_Software/apache-maven-3.9.6/bin/mvn install'
	                 }}
	    stage('Deployment'){
		 steps {
			script {
			 if ( env.choice == 'QA' ){
        	sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_software/apache-tomcat-9.0.88/webapps'
        	echo "deployment has been done on QA!"
			 }
			else ( env.choice == 'UAT' ){
    		sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_software/apache-tomcat-9.0.88/webapps'
        	echo "deployment has been done on UAT!"
			}
			}}}
}}
