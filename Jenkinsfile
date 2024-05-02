pipeline {
	agent any  
	parameters {
  choice (choices: ['QA', 'UAT', 'DEV'], description: 'select the environment', name: 'choice')
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
			       sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
			       }
			  else ( env.choice == 'UAT' ){
			       sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
			       }
			}}}	
}}
