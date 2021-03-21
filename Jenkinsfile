pipeline {
  agent any
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
  
