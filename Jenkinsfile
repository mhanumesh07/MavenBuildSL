pipeline {
	agent any
	
	stages{
		stage('Checkout Code'){
			steps{
				checkout scm
				}
			}
	
	stage('Build'){
		steps{
			 sh 'mvn -Dmaven.test.failure.ignore=true clean package'
		}


	}
	
	stage('Archive Artifact'){
		steps{
		archiveArtifacts artifacts:'target/*.war'
		}
	}
	
	stage('deployment'){
		steps{
		//deploy adapters: [tomcat9(credentialsId: 'TomcatCreds' path: '', url: 'http://52.90.187.236:8080/')], contextPath: 'counterwebapp', war: 'target/*.war'
		deploy adapters: [tomcat9(url: 'http://3.26.226.9:8080/', 
                              credentialsId: 'tomcat-ID')], 
                     war: 'target/*.war',
                     contextPath: 'app'
		}
		
	}
	

	}
}
