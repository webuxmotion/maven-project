pipeline {
  agent any
  triggers {
    pollSCM('*/5 * * * *')
  }
  tools {
    maven 'localMaven'
    jdk 'localJDK'
  }
  stages{
    stage ('Build'){
      steps {
        sh 'mvn clean package'
      }
      post {
        success {
          echo 'Archiving...'
          archiveArtifacts artifacts:'**/target/*.war'
        }
      }
    }
    stage ('Deployments') {
      parallel {
        stage ('Deploy to Staging') {
          steps {
            sh "cp **/target/*.war /usr/local/Cellar/tomcat/tomcat-staging/webapps"
          }
        }
      }
    }
  }
} 
  
