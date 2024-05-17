pipeline {
	agent any  
	parameters {
  choice (choices: ['QA', 'UAT', 'DEV'], description: 'select the environment', name: 'choice')
        }
        triggers {
           pollSCM '* * * * *'
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
			       echo "DEPLOYMENT SUCCESSFULL ON QA SERVER"
			       }
			  else ( env.choice == 'UAT' ){
			       sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
			       echo "DEPLOYMENT SUCCESSFULL ON UAT SERVER"
			       }
			}}}
			stage('slack-notification'){
		   steps {
		      slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#notify', color: 'good', message: 'SLACK NOTIFICATION JOB CREATED', teamDomain: 'MyDevOpsTeam', tokenCredentialId: '05c23611-4a79-4a45-8813-46c26cd00d99'
		     }}	
        }}
