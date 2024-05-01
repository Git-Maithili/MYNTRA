pipeline {
    agent any 
    
    parameters {
        choice(name: 'ENV', choices: ['QA', 'UAT'], description: 'Select the environment')
    }
    
    triggers {
        pollSCM '* * * * *'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh '/home/vboxuser/Documents/DevOps_Software/apache-maven-3.9.6/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                script {
                    if (env.ENV == 'QA') {
                        sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
                        echo "Deployment has been COMPLETED on QA!"
                    } else if (env.ENV == 'UAT') {
                        sh 'cp target/MYNTRA.war /home/vboxuser/Documents/DevOps_Software/apache-tomcat-9.0.88/webapps'
                        echo "Deployment has been done on UAT!"
                    }
                }
                stage('Slack') {
            steps {
                sh 'slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'notifyme', message: 'Welcome to Grras', notifyCommitters: true, teamDomain: 'MyDevOpsTeam'
            }
           }       
        }
    }
}
