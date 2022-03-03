pipeline
{
 agent any 
	 environment{
	    connAppclientId=credentials('connectedAppclientid')
              connAppclientSecret=credentials('connectedAppclientsecret')
              connAppgrantType='client_credentials'
		  }
     

 stages{
    stage('Build Application'){
    steps{
    bat 'mvn clean install'
    }
    }
    
    stage('Mule Test Application'){
    steps{
     bat 'mvn clean test'
    }
    }
    
    
   
   stage('Deploy Application in Mulesoft Cloudhub'){
   steps{
   bat 'mvn clean package deploy -DmuleDeploy -DconnectedAppClientId = ${connAppclientId} -DconnectedAppClientSecret = ${connAppclientSecret} -DconnectedAppGrantType = ${connAppgrantType}'
   }
   }
  }
}

