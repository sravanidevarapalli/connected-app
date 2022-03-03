pipeline
{
 agent any 
     

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
   environment{
	    connAppclientId=credentials('connectedAppclientid')
              connAppclientSecret=credentials('connectedAppclientsecret')
              connAppgrantType='client_credentials'
		  }
		
            
   steps{
   bat 'mvn package deploy -DmuleDeploy -DconnectedAppClientId = ${connAppclientId} -DconnectedAppClientSecret = ${connAppclientSecret} -DconnectedAppGrantType = ${connAppgrantType}'
   }
   }
  }
}

