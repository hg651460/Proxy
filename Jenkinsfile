pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
            stage('Clean') {
                steps {
		dir('forecastweatherapi') {
		sh "mvn clean"
		}
	    }
	}
		
            stage('Build proxy bundle') {
                steps {
                    dir('forecastweatherapi') {
                    sh "mvn package -Ptest -Denv=${params.apigee_env} -Dorg=${params.apigee_org}"

                }
            }
        }		

   	 stage('Deploy proxy bundle') {
		steps {
	    	    dir('forecastweatherapi') {
	   	    sh "mvn install -Ptest -Denv=${params.apigee_env} -Dorg=${params.apigee_org} -Dusername=${params.apigee_user} -Dpassword=${params.apigee_pwd}"
	
		}
    	     }
   	}
  }
}
