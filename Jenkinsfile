pipeline {
  agent any
  tools { 
        maven 'Maven 3.6.3' 
        jdk 'adoptopenjdk-11' 
  }
  stages{
       stage ('Build'){
        steps {
          sh 'mvn clean package'
        }
       }
       stage ('Deployments') {
         steps {
          sh 'Deploy step...'
        }
       }
    }
} 
  
