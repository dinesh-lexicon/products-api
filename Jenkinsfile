pipeline {
  agent any
  
  environment{
  	anypoint_creds= credentials('anypoint_creds')
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
	 	bat 'mvn -U -e -V -B DskipTests -Pdev deploy -DmuleDeploy -Dusername="%anypoint_creds_USR%" -Dpassword="%anypoint_creds_PSW%" -Danypoint.platform.client_id="%CLIENT_ID_DEV%" -Danypoint.platform.client_secret="%CLIENT_SECRET_DEV%"'
	 }
    }
   
  }
}