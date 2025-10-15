pipeline {

    agent any
    stages {
	
        stage('CLONE SCM') {
            steps {
                echo 'This stage clones SC from GIT repo'				
				git branch: 'main', url: 'https://github.com/kmanasagithub/mindcircuit16d.git'
            }
        }
		
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'			
				
            }
        }
		
        stage('Deploy to Tomcat') {
            steps {
                echo 'This stage deploys .war to tomcat webserver'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://34-234-79-114:8080')], contextPath: 'Manasa_Pipleline_pro', war: '**/*.war'
            }
        }		
		
    }
}
