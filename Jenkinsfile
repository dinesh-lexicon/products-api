pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
          bat "mvn test"
      }
    }

     stage('Deployment') {
      steps {
          bat "mvn -U -e -V -B DskipTests -Pdev deploy -DmuleDeploy"
      }
    }
   
  }
}