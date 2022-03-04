pipeline
{
 agent any 
	 environment{
	    connAppclientId=credentials('connectedAppclientid')
              connAppclientSecret=credentials('connectedAppclientsecret')
              connAppgrantType='client_credentials'
		  }
     

 stages{
   stage('Build') {
            steps {
              bat  "mvn clean -U install -DskipTests"
            
        }
        }
    
    
   
   stage('Deploy Application in Mulesoft Cloudhub'){
   steps{
   bat 'mvn clean package deploy -DmuleDeploy -DconnectedAppClientId = ${connAppclientId} -DconnectedAppClientSecret = ${connAppclientSecret} -DconnectedAppGrantType = ${connAppgrantType}'
   }
   }
  }
}

