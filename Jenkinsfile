pipeline {
  agent any
  
  environment{
  	ANYPOINT_CREDS= credentials('anypoint_creds')
  }
  
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          echo  "**************Munit Test cases execution************"
      }
    }

     stage('Deployment') {
     
	 environment{
		CLIENT_ID_DEV= credentials('client_id_dev')
		CLIENT_SECRET_DEV=credentials('client_secret_dev')
	 }
	 steps {
	 	bat 'mvn -U -e -V -B -DskipTests -Pdev deploy -DmuleDeploy -Dusername="%ANYPOINT_CREDS_USR%" -Dpassword="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID_DEV%" -Danypoint.platform.client_secret="%CLIENT_SECRET_DEV%"'
	 }
    }
   
  }
}