
pipeline {
    agent any 
    stages {
        stage('ContinuousDownload') {
            steps {
                git 'https://github.com/amarroy87/JenkinsFiles.git'
            }
        }
		stage('ContinuousBuild') {
            steps {
                sh 'mvn package'
            }
        }
		stage('ContinuousDeployment') {
            steps {
                sh 'scp /home/vagrant/.jenkins/workspace/samplepipeline1/webapp/target/webapp.war vagrant@10.0.0.32:/var/lib/tomcat7/webapps/qaenv.war'
            }
        }
		stage('ContinuousTesting') {
            steps {
                git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        sh 'java -jar /home/vagrant/.jenkins/workspace/samplepipeline1/testing.jar' 
            }
        }		
		
		}
	post
	{
	    success
		{
        sh 'scp /home/vagrant/.jenkins/workspace/samplepipeline1/webapp/target/webapp.war vagrant@10.0.0.33:/var/lib/tomcat7/webapps/prodenv.war'
		}
		
		
    }		
	
	}
