pipeline {
	agent any  
	parameters {
  string (defaultValue: 'QA', description: 'enter QA or UAT', name: 'ENV')
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
			  if ( env.ENV == 'QA' ){
			       sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
			       }
			  else ( env.ENV == 'UAT' ){
			       sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
			       }
			}}}	
}}
