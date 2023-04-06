pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
    
   stages{
    /*stage('CompileandRunSonarAnalysis') {
            steps {	
            echo "testing"
		        sh 'mvn clean verify sonar:sonar -Dsonar.projectKey= -Dsonar.organization=rayudusubrahmanyam12 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=03284155ab46de9bcfce7f5c1fe8c488e0021d8c'
			}
    }*/

  stage('SonarCloud') {
  environment {
    SCANNER_HOME = tool 'SonarQubeScanner'
    ORGANIZATION = "rayudusubrahmanyam12"
    PROJECT_NAME = "aws-terraform-jenkins-k8s-security"
  }
  steps {
    withSonarQubeEnv(installationName: 'SonarCloudServer', credentialsId: 'SonarQubeServerToken') {
        sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$ORGANIZATION \
        -Dsonar.java.binaries=build/classes/java/ \
        -Dsonar.projectKey=$PROJECT_NAME \
        -Dsonar.sources=.'''
    }
  }
}


	/*stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }	*/	
  }
}