pipeline {
  agent any
  triggers {
    pollSCM('*/1 * * * *')
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
        stage ('Deploy to Prod') {
          steps {
            timeout(time:5, unit:'DAYS') {
              input message:'Approve Prod Deployment?'
            }
            sh "cp **/target/*.war /usr/local/Cellar/tomcat/tomcat-prod/webapps"
          }
        }
      }
    }
  }
} 
  
