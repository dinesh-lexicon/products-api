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
  		client_id_dev= credentials('client_id_dev')
  		client_secret_dev=credentials('client_secret_dev')
  	}
      steps {
          bat 'mvn -U -e -V -B DskipTests -Pdev deploy -DmuleDeploy -Dusername="%anypoint_creds%" -Dpassword="%anypoint_creds%" -Danypoint.platform.client_id="%client_id_dev%" -Danypoint.platform.client_secret="%client_secret_dev%"'
      }
    }
   
  }
}