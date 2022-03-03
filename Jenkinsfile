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
		      connAppclientId=credentials('connAppclientid')
              connAppclientSecret=credentials('connAppclientsecret')
              connAppgrantType='client_credentials'
		  }
		  when {
                branch 'Sandbox' 
            }
   steps{
   bat 'mvn package deploy -DmuleDeploy -DconnectedAppClientId = ${connAppclientId} -DconnectedAppClientSecret = ${connAppclientSecret}
   -DconnectedAppGrantType = ${connAppgrantType}'
   }
   }
  }
}
